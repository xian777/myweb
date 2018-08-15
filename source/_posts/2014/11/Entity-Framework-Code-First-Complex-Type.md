---
title: Entity Framework Code First Complex Type
tags:
  - Code First
  - Entity Framework
date: 2014-11-25 18:25:00
---

Complex Type是用來重覆使用的欄位，有幾個規定
1\. 不能有主索引
2\. 一個類別中只能有一個實體
3\. 只能是引用屬性，不能是集合屬性

Table1
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    public class Table1
    {
        public int Table1Id { get; set; }
        public Address Address { get; set; }
    }
}
</pre></div>
Table2
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    public class Table2
    {
        public int Table2Id { get; set; }
        public Address Address { get; set; }
    }
}
</pre></div>
Address
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    public class Address
    {
        public string Addr1 { get; set; }

        public string Addr2 { get; set; }
    }
}
</pre></div>
預設狀態資料表的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-VUdYb_36M7Y/VHRZEfTanyI/AAAAAAAABxc/9lM5jwJEEXg/s1600/01.png)](http://2.bp.blogspot.com/-VUdYb_36M7Y/VHRZEfTanyI/AAAAAAAABxc/9lM5jwJEEXg/s1600/01.png)</div>
加上DataAnnotation
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.ComponentModel.DataAnnotations.Schema;

    [ComplexType]
    public class Address
    {
        [Column("Addr1")]
        public string Addr1 { get; set; }

        [Column("Addr2")]

        public string Addr2 { get; set; }
    }
}
</pre></div>
Fluent API設定
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Data.Entity;
    using System.Data.Entity.ModelConfiguration;

    public class DemoContext : DbContext
    {
        public DbSet&lt;Table1&gt; Table1 { get; set; }
        public DbSet&lt;Table2&gt; Table2 { get; set; }

        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
            modelBuilder.Configurations.Add(new AddressConfiguration());
        }

        private class AddressConfiguration : ComplexTypeConfiguration&lt;Address&gt;
        {
            public AddressConfiguration()
            {
                this.Property(x =&gt; x.Addr1).HasColumnName("Addr1");
                this.Property(x =&gt; x.Addr2).HasColumnName("Addr2");
            }
        }
    }
}
</pre></div>
加上設定後資料表的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-SrcjXxIdxHs/VHRZH1IT_rI/AAAAAAAABxk/Hp82tQKWg18/s1600/02.png)](http://3.bp.blogspot.com/-SrcjXxIdxHs/VHRZH1IT_rI/AAAAAAAABxk/Hp82tQKWg18/s1600/02.png)</div>