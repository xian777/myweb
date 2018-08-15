---
title: Entity Framework DbContext 新增、修改、刪除、查詢
tags:
  - DbContext
  - Entity Framework
date: 2014-12-17 15:33:00
---

首先建立一個留言版的資料庫來當例子

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

</pre></div>留言版明細表
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
新增、修改、刪除、查詢
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System.Collections.Generic;
    using System.Data.Entity;
    using System.Linq;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new DropCreateDatabaseAlways&lt;DemoContext&gt;());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);
            }

            // 新增
            using (DemoContext db = new DemoContext())
            {
                db.Topic.Add(new Topic
                {
                    TopicTitle = "a",
                    Reply = new List&lt;Reply&gt;
                    {
                        new Reply { ReplyMessage = "a1" },
                        new Reply { ReplyMessage = "a2" },
                        new Reply { ReplyMessage = "a3" },
                    }
                });

                db.SaveChanges();
            }

            // 修改
            using (DemoContext db = new DemoContext())
            {
                var model = db.Topic.FirstOrDefault();
                if (model != null)
                {
                    model.TopicTitle = "modify";
                    db.SaveChanges();
                }
            }

            // 查詢
            using (DemoContext db = new DemoContext())
            {
                var model1 = db.Topic.Find(1);
                var model2 = db.Topic.SingleOrDefault();
                var model3 = db.Topic.FirstOrDefault();
            }

            // 刪除
            using (DemoContext db = new DemoContext())
            {
                var model = new Topic { TopicId = 1 };
                db.Entry(model).State = EntityState.Deleted;
                db.SaveChanges();
            }
        }
    }
}
</pre></div>
新增的SQL
<div><pre class="brush:sql">exec sp_reset_connection
go
exec sp_executesql N'INSERT [dbo].[Topic]([TopicTitle])
VALUES (@0)
SELECT [TopicId]
FROM [dbo].[Topic]
WHERE @@ROWCOUNT &gt; 0 AND [TopicId] = scope_identity()',N'@0 nvarchar(max) ',@0=N'a'
go
exec sp_executesql N'INSERT [dbo].[Reply]([TopicId], [ReplyMessage])
VALUES (@0, @1)
SELECT [ReplyId]
FROM [dbo].[Reply]
WHERE @@ROWCOUNT &gt; 0 AND [ReplyId] = scope_identity()',N'@0 int,@1 nvarchar(max) ',@0=1,@1=N'a1'
go
exec sp_executesql N'INSERT [dbo].[Reply]([TopicId], [ReplyMessage])
VALUES (@0, @1)
SELECT [ReplyId]
FROM [dbo].[Reply]
WHERE @@ROWCOUNT &gt; 0 AND [ReplyId] = scope_identity()',N'@0 int,@1 nvarchar(max) ',@0=1,@1=N'a2'
go
exec sp_executesql N'INSERT [dbo].[Reply]([TopicId], [ReplyMessage])
VALUES (@0, @1)
SELECT [ReplyId]
FROM [dbo].[Reply]
WHERE @@ROWCOUNT &gt; 0 AND [ReplyId] = scope_identity()',N'@0 int,@1 nvarchar(max) ',@0=1,@1=N'a3'
go

</pre></div>
修改的SQL
<div><pre class="brush:sql">exec sp_reset_connection
go
SELECT TOP (1) 
    [c].[TopicId] AS [TopicId], 
    [c].[TopicTitle] AS [TopicTitle]
    FROM [dbo].[Topic] AS [c]
go
exec sp_reset_connection
go
exec sp_executesql N'UPDATE [dbo].[Topic]
SET [TopicTitle] = @0
WHERE ([TopicId] = @1)
',N'@0 nvarchar(max) ,@1 int',@0=N'modify',@1=1
go

</pre></div>
查詢的SQL
<div><pre class="brush:sql">exec sp_reset_connection
go
exec sp_executesql N'SELECT TOP (2) 
    [Extent1].[TopicId] AS [TopicId], 
    [Extent1].[TopicTitle] AS [TopicTitle]
    FROM [dbo].[Topic] AS [Extent1]
    WHERE [Extent1].[TopicId] = @p0',N'@p0 int',@p0=1
go
exec sp_reset_connection
go
SELECT TOP (2) 
    [c].[TopicId] AS [TopicId], 
    [c].[TopicTitle] AS [TopicTitle]
    FROM [dbo].[Topic] AS [c]
go
exec sp_reset_connection
go
SELECT TOP (1) 
    [c].[TopicId] AS [TopicId], 
    [c].[TopicTitle] AS [TopicTitle]
    FROM [dbo].[Topic] AS [c]
go
</pre></div><div>
</div>
刪除的SQL 
<div><pre class="brush:sql">exec sp_reset_connection
go
exec sp_executesql N'DELETE [dbo].[Topic]
WHERE ([TopicId] = @0)',N'@0 int',@0=1
go
</pre></div>