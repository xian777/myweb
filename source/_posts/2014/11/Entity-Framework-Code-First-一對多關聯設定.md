---
title: Entity Framework Code First 一對多關聯設定
tags:
  - Code First
  - Entity Framework
date: 2014-11-25 16:17:00
---

兩個類別之間，一個包含集合導覽屬性，一個包含引用屬性，就會被當成一對多關系

主表
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Topic")]
    public class Topic
    {
        public int TopicId { get; set; }

        public string Title { get; set; }

        public virtual ICollection&lt;Reply&gt; Reply { get; set; }
    }
}
</pre></div>
明細表
外鍵的命名只有符合預設的規則，就會建立關系，規則如下
1\. 目標類型索引的名稱
2\. 目標類型名稱+目標類型主索引名稱
3\. 導覽屬性名稱+目標類型主索引名稱
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Reply")]
    public class Reply
    {
        public int ReplyId { get; set; }

        public int TopicId { get; set; }
        // public int TopicTopicId { get; set; }
        // public int TheTopicTopicId { get; set; }

        public string Title { get; set; }

        public virtual Topic TheTopic { get; set; }
    }
}
</pre></div>
若不是用預設規則的命名方式，可以透過ForeignKey這個Attribute設定
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Reply")]
    public class Reply
    {
        public int ReplyId { get; set; }

        [ForeignKey("TheTopic")]
        public int tid { get; set; }

        public string Title { get; set; }

        public virtual Topic TheTopic { get; set; }
    }
}
</pre></div>
也可以設定在引用屬性上
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Reply")]
    public class Reply
    {
        public int ReplyId { get; set; }

        public int tid { get; set; }

        public string Title { get; set; }

        [ForeignKey("tid")]
        public virtual Topic TheTopic { get; set; }
    }
}
</pre></div>
透過FluentAPI設定方式
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Data.Entity;

    public class DemoContext : DbContext
    {
        public DbSet&lt;Topic&gt; Topic { get; set; }

        public DbSet&lt;Reply&gt; Reply { get; set; }

        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
            modelBuilder.Entity&lt;Topic&gt;()
                .HasMany(x =&gt; x.Reply)
                .WithRequired(x =&gt; x.TheTopic)
                .HasForeignKey(x =&gt; x.tid)
                .WillCascadeOnDelete(true);
        }
    }
}
</pre></div>
資料表建立的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-x8Be3G5KSmE/VHQ8NnYctyI/AAAAAAAABwk/2MeEYOuWK8c/s1600/01.png)](http://4.bp.blogspot.com/-x8Be3G5KSmE/VHQ8NnYctyI/AAAAAAAABwk/2MeEYOuWK8c/s1600/01.png)</div>
關聯圖
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-h0YFZrs6BNg/VHQ8RG_hqqI/AAAAAAAABws/K-w1Qjy3owY/s1600/02.png)](http://3.bp.blogspot.com/-h0YFZrs6BNg/VHQ8RG_hqqI/AAAAAAAABws/K-w1Qjy3owY/s1600/02.png)</div>