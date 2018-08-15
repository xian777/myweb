---
title: Entity Framework DbContext 延遲加載、貪婪加載、顯性加載
tags:
  - DbContext
  - Entity Framework
date: 2014-12-17 16:26:00
---

用一個留言版的主表和明細表當例子，順便加入初始化資料來方便觀察資料載入方式的差異
DemoContext
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Data.Entity;

    public class DemoContext : DbContext
    {
        public DbSet&lt;Topic&gt; Topic { get; set; }
        public DbSet&lt;Reply&gt; Reply { get; set; }
    }
}
</pre></div>
留言版主表
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Topic")]
    public class Topic
    {
        [Key]
        public int TopicId { get; set; }
        public string TopicTitle { get; set; }
        public virtual ICollection&lt;Reply&gt; Reply { get; set; }
    }
}

</pre></div>
留言版明細表
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Reply")]
    public class Reply
    {
        [Key]
        public int ReplyId { get; set; }
        [ForeignKey("Topic")]
        public int TopicId { get; set; }
        public string ReplyMessage { get; set; }
        public virtual Topic Topic { get; set; }
    }
}
</pre></div>
資料初始化
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Collections.Generic;
    using System.Data.Entity;

    public class MyInit : DropCreateDatabaseAlways&lt;DemoContext&gt;
    {
        protected override void Seed(DemoContext context)
        {
            context.Topic.AddRange(
                new List&lt;Topic&gt;
                {
                    new Topic
                    {
                        TopicTitle = "a",
                        Reply = new List&lt;Reply&gt;
                        {
                            new Reply { ReplyMessage = "a1" },
                            new Reply { ReplyMessage = "a2" },
                            new Reply { ReplyMessage = "a3" },
                        }
                    },
                    new Topic
                    {
                        TopicTitle = "b",
                        Reply = new List&lt;Reply&gt;
                        {
                            new Reply { ReplyMessage = "b1" },
                            new Reply { ReplyMessage = "b2" },
                            new Reply { ReplyMessage = "b3" },
                        }
                    },
                    new Topic
                    {
                        TopicTitle = "c",
                        Reply = new List&lt;Reply&gt;
                        {
                            new Reply { ReplyMessage = "c1" },
                            new Reply { ReplyMessage = "c2" },
                            new Reply { ReplyMessage = "c3" },
                        }
                    },
                    new Topic
                    {
                        TopicTitle = "d"
                    }
                });
        }
    }
}

</pre></div>產生的資料
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-lXLfCqetSgg/VJE6AR4O1II/AAAAAAAABy8/fuU-yncOXuw/s1600/%E7%94%A2%E7%94%9F%E7%9A%84%E8%B3%87%E6%96%99.png)](http://4.bp.blogspot.com/-lXLfCqetSgg/VJE6AR4O1II/AAAAAAAABy8/fuU-yncOXuw/s1600/%E7%94%A2%E7%94%9F%E7%9A%84%E8%B3%87%E6%96%99.png)</div>

延遲加載利用遠端代理模式，必須在導覽屬性上使用virtual關鍵字，才會在存取到這個屬性時，動態去建立相對應的類別
這種方式比較明顯的缺點，是會分段產生SQL語法，還有就是在取資料的時後，雖然有加入過濾的條件，但是最後產生的SQL語法，還是會取回全部的資料，然後才在記憶體中過濾資料

<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;
    using System.Linq;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new MyInit());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                foreach (var topic in db.Topic)
                {
                    foreach (var reply in topic.Reply.Where(x=&gt;x.ReplyMessage.Contains("1")))
                    {
                        Console.WriteLine("title:{0}, message:{1}", topic.TopicTitle, reply.ReplyMessage);
                    }
                }
            }
        }
    }
}
</pre></div>
延遲加載產生的SQL語法
<div><pre class="brush:sql">SELECT 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[TopicTitle] AS [TopicTitle]
    FROM [dbo].[Topic] AS [Extent1]
go
exec sp_executesql N'SELECT 
    [Extent1].[ReplyId] AS [ReplyId], 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[ReplyMessage] AS [ReplyMessage]
    FROM [dbo].[Reply] AS [Extent1]
    WHERE [Extent1].[TopicId] = @EntityKeyValue1',N'@EntityKeyValue1 int',@EntityKeyValue1=1
go
exec sp_executesql N'SELECT 
    [Extent1].[ReplyId] AS [ReplyId], 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[ReplyMessage] AS [ReplyMessage]
    FROM [dbo].[Reply] AS [Extent1]
    WHERE [Extent1].[TopicId] = @EntityKeyValue1',N'@EntityKeyValue1 int',@EntityKeyValue1=2
go
exec sp_executesql N'SELECT 
    [Extent1].[ReplyId] AS [ReplyId], 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[ReplyMessage] AS [ReplyMessage]
    FROM [dbo].[Reply] AS [Extent1]
    WHERE [Extent1].[TopicId] = @EntityKeyValue1',N'@EntityKeyValue1 int',@EntityKeyValue1=3
go
exec sp_executesql N'SELECT 
    [Extent1].[ReplyId] AS [ReplyId], 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[ReplyMessage] AS [ReplyMessage]
    FROM [dbo].[Reply] AS [Extent1]
    WHERE [Extent1].[TopicId] = @EntityKeyValue1',N'@EntityKeyValue1 int',@EntityKeyValue1=4
go

</pre></div>
貪婪加載是產生Join的語法，在一次SQL查詢中就取回所有的資料
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;
    using System.Linq;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new MyInit());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                foreach (var topic in db.Topic.Include(x =&gt; x.Reply))
                {
                    foreach (var reply in topic.Reply.Where(x =&gt; x.ReplyMessage.Contains("1")))
                    {
                        Console.WriteLine("title:{0}, message:{1}", topic.TopicTitle, reply.ReplyMessage);
                    }
                }
            }
        }
    }
}
</pre></div>
產生的SQL語法
<div><pre class="brush:sql">SELECT 
    [Project1].[TopicId] AS [TopicId], 
    [Project1].[TopicTitle] AS [TopicTitle], 
    [Project1].[C1] AS [C1], 
    [Project1].[ReplyId] AS [ReplyId], 
    [Project1].[TopicId1] AS [TopicId1], 
    [Project1].[ReplyMessage] AS [ReplyMessage]
    FROM ( SELECT 
        [Extent1].[TopicId] AS [TopicId], 
        [Extent1].[TopicTitle] AS [TopicTitle], 
        [Extent2].[ReplyId] AS [ReplyId], 
        [Extent2].[TopicId] AS [TopicId1], 
        [Extent2].[ReplyMessage] AS [ReplyMessage], 
        CASE WHEN ([Extent2].[ReplyId] IS NULL) THEN CAST(NULL AS int) ELSE 1 END AS [C1]
        FROM  [dbo].[Topic] AS [Extent1]
        LEFT OUTER JOIN [dbo].[Reply] AS [Extent2] ON [Extent1].[TopicId] = [Extent2].[TopicId]
    )  AS [Project1]
    ORDER BY [Project1].[TopicId] ASC, [Project1].[C1] ASC
</pre></div>
顯性加載也是分段式的語法，和延遲加載的差別在於，延遲加載必須先取回導覽屬性的全部資料，才能繼續後續的處理，而顯性加載則可以篩選要取回那些資料
透過Entry取得實體後，Collection是取集合對應的屬性，Reference是取實體對應的屬性
db.Configuration.LazyLoadingEnabled是用來指定是否要啟用延遲加載，預設是啟用的

<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;
    using System.Linq;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new MyInit());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);
                db.Configuration.LazyLoadingEnabled = false;

                foreach (var topic in db.Topic)
                {
                    db.Entry(topic).Collection(x =&gt; x.Reply)
                        .Query()
                        .Where(x =&gt; x.ReplyMessage.Contains("1"))
                        .Load();

                    if (topic.Reply != null)
                    {
                        foreach (var reply in topic.Reply)
                        {
                            Console.WriteLine("title:{0}, message:{1}", topic.TopicTitle, reply.ReplyMessage);
                        }
                    }
                }
            }
        }
    }
}
</pre></div>
產生的SQL語法
<div><pre class="brush:sql">SELECT 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[TopicTitle] AS [TopicTitle]
    FROM [dbo].[Topic] AS [Extent1]
go
exec sp_executesql N'SELECT 
    [Extent1].[ReplyId] AS [ReplyId], 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[ReplyMessage] AS [ReplyMessage]
    FROM [dbo].[Reply] AS [Extent1]
    WHERE ([Extent1].[TopicId] = @EntityKeyValue1) AND ([Extent1].[ReplyMessage] LIKE N''%1%'')',N'@EntityKeyValue1 int',@EntityKeyValue1=1
go
exec sp_executesql N'SELECT 
    [Extent1].[ReplyId] AS [ReplyId], 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[ReplyMessage] AS [ReplyMessage]
    FROM [dbo].[Reply] AS [Extent1]
    WHERE ([Extent1].[TopicId] = @EntityKeyValue1) AND ([Extent1].[ReplyMessage] LIKE N''%1%'')',N'@EntityKeyValue1 int',@EntityKeyValue1=2
go
exec sp_executesql N'SELECT 
    [Extent1].[ReplyId] AS [ReplyId], 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[ReplyMessage] AS [ReplyMessage]
    FROM [dbo].[Reply] AS [Extent1]
    WHERE ([Extent1].[TopicId] = @EntityKeyValue1) AND ([Extent1].[ReplyMessage] LIKE N''%1%'')',N'@EntityKeyValue1 int',@EntityKeyValue1=3
go
exec sp_executesql N'SELECT 
    [Extent1].[ReplyId] AS [ReplyId], 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[ReplyMessage] AS [ReplyMessage]
    FROM [dbo].[Reply] AS [Extent1]
    WHERE ([Extent1].[TopicId] = @EntityKeyValue1) AND ([Extent1].[ReplyMessage] LIKE N''%1%'')',N'@EntityKeyValue1 int',@EntityKeyValue1=4
go

</pre></div>