---
title: Entity Framework Code First 多對多關聯設定
tags:
  - Code First
  - Entity Framework
date: 2014-11-25 16:48:00
---

兩個類別之間，各自包含對應的集合導覽屬性，就會被當成多對多關系
在資料庫中的多對多關系，需要用三張表來表示，分別是一對多再多對一

一個使用者可以有多個群組
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("User")]
    public class User
    {
        public int UserId { get; set; }

        public string UserName { get; set; }

        public virtual ICollection&lt;Group&gt; Group { get; set; }
    }
}
</pre></div>
一個群組可以有多個使用者
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Group")]
    public class Group
    {
        public int GroupId { get; set; }

        public string GroupName { get; set; }

        public virtual ICollection&lt;User&gt; User { get; set; }
    }
}
</pre></div>
預設會自動生成第三張表
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Kf0FCZt6HKU/VHQ_vKY2CbI/AAAAAAAABw4/vmkQa6Gjf08/s1600/01.png)](http://4.bp.blogspot.com/-Kf0FCZt6HKU/VHQ_vKY2CbI/AAAAAAAABw4/vmkQa6Gjf08/s1600/01.png)</div>

透過FluentAPI設定第三張表的名稱，和欄位名稱
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Data.Entity;

    public class DemoContext : DbContext
    {
        public DbSet&lt;User&gt; User { get; set; }

        public DbSet&lt;Group&gt; Group { get; set; }

        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
            modelBuilder.Entity&lt;User&gt;()
                .HasMany(x =&gt; x.Group)
                .WithMany(x =&gt; x.User)
                .Map(x =&gt;{
                    x.ToTable("MyUserGroup");
                    x.MapLeftKey("UserID");
                    x.MapRightKey("GroupID");
                });
        }
    }
}
</pre></div>
資料表建立的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-pPz9en0LdGs/VHRB1DkAGRI/AAAAAAAABxE/bn58i66WkR0/s1600/03.png)](http://2.bp.blogspot.com/-pPz9en0LdGs/VHRB1DkAGRI/AAAAAAAABxE/bn58i66WkR0/s1600/03.png)</div>
關聯圖
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ge9m8hgR2NE/VHRCAxbu4CI/AAAAAAAABxM/dWik0q60CHA/s1600/04.png)](http://2.bp.blogspot.com/-ge9m8hgR2NE/VHRCAxbu4CI/AAAAAAAABxM/dWik0q60CHA/s1600/04.png)</div>