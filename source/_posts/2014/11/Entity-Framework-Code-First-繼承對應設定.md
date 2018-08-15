---
title: Entity Framework Code First 繼承對應設定
tags:
  - Code First
  - Entity Framework
date: 2014-11-26 11:50:00
---

TPH(Table Per Hierarchy)
基底類別和衍生類別都映射到同一張表中，通過一個鑒別欄位來識別資料是屬於基底或是衍生類別，這是預設的映射方法

Table1 
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.ComponentModel.DataAnnotations;

    public class Table1
    {
        [Key]
        public int Table1Id { get; set; }

        public int C1 { get; set; }

        public int C2 { get; set; }
    }
}
</pre></div>
Table2 
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    public class Table2 : Table1
    {
        public int C3 { get; set; }

        public int C4 { get; set; }
    }
}
</pre></div>
新增幾筆資料 
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;

    class Program
    {
        static void Main(string[] args)
        {
            using (DemoContext db = new DemoContext())
            {
                db.Table1.Add(new Table1 { C1 = 1, C2 = 2 });
                db.Table2.Add(new Table2 { C1 = 1, C2 = 2, C3 = 3, C4 = 4 });
                db.SaveChanges();
            }
        }
    }
}
</pre></div>
TPH資料表建立的樣子
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-yXePG-77UcQ/VHVNiZMIatI/AAAAAAAABx8/J6Wst3vpqJE/s1600/01.TPH%E8%B3%87%E6%96%99%E8%A1%A8.png)](http://1.bp.blogspot.com/-yXePG-77UcQ/VHVNiZMIatI/AAAAAAAABx8/J6Wst3vpqJE/s1600/01.TPH%E8%B3%87%E6%96%99%E8%A1%A8.png)</div>
TPH資料儲存的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-sI3daA47kAs/VHVNlgPjziI/AAAAAAAAByE/GIZvaaEy7Yo/s1600/02.TPH%E8%B3%87%E6%96%99%E5%85%A7%E5%AE%B9.png)](http://1.bp.blogspot.com/-sI3daA47kAs/VHVNlgPjziI/AAAAAAAAByE/GIZvaaEy7Yo/s1600/02.TPH%E8%B3%87%E6%96%99%E5%85%A7%E5%AE%B9.png)</div>
可以透過Fluent API設定用來識別的欄位，和識別資料的值
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Data.Entity;

    public class DemoContext : DbContext
    {
        public DbSet&lt;Table1&gt; Table1 { get; set; }
        public DbSet&lt;Table2&gt; Table2 { get; set; }

        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
            modelBuilder.Entity&lt;Table1&gt;()
                .Map(x=&gt; {
                    x.ToTable("Table1");
                    x.Requires("QQ").HasValue("AA");
                })
                .Map&lt;Table2&gt;(x=&gt; {
                    x.Requires("QQ").HasValue("BB");
                });
        }
    }
}
</pre></div>
設定後資料儲存的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ro-xCLfW2Zw/VHVNpJm_mYI/AAAAAAAAByM/iX8TGskajsY/s1600/03.%E8%A8%AD%E5%AE%9A%E5%BE%8C%E7%9A%84%E6%A8%A3%E5%AD%90.png)](http://2.bp.blogspot.com/-ro-xCLfW2Zw/VHVNpJm_mYI/AAAAAAAAByM/iX8TGskajsY/s1600/03.%E8%A8%AD%E5%AE%9A%E5%BE%8C%E7%9A%84%E6%A8%A3%E5%AD%90.png)</div>

TPT(Table Per Type)
把資料映射到各自的資料表中，並在衍生類別的資料表中自動生成外鍵來關聯基厎類別的資料表，使用方式很簡單，只要指定各自資料表的名稱就行了
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Data.Entity;

    public class DemoContext : DbContext
    {
        public DbSet&lt;Table1&gt; Table1 { get; set; }
        public DbSet&lt;Table2&gt; Table2 { get; set; }

        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
            modelBuilder.Entity&lt;Table1&gt;().ToTable("Table1");
            modelBuilder.Entity&lt;Table2&gt;().ToTable("Table2");
        }
    }
}
</pre></div>
TPT資料表建立的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-BqWRzzWB3I8/VHVNtXjUhCI/AAAAAAAAByU/hM-sHRUu8wo/s1600/04.TPT%E8%B3%87%E6%96%99%E8%A1%A8.png)](http://2.bp.blogspot.com/-BqWRzzWB3I8/VHVNtXjUhCI/AAAAAAAAByU/hM-sHRUu8wo/s1600/04.TPT%E8%B3%87%E6%96%99%E8%A1%A8.png)</div>
TPT資料儲存的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-X_82GktPX9s/VHVN1eeGhWI/AAAAAAAAByc/Vo65h_II8J0/s1600/05.TPT%E8%B3%87%E6%96%99%E5%85%A7%E5%AE%B9.png)](http://3.bp.blogspot.com/-X_82GktPX9s/VHVN1eeGhWI/AAAAAAAAByc/Vo65h_II8J0/s1600/05.TPT%E8%B3%87%E6%96%99%E5%85%A7%E5%AE%B9.png)</div>

TPC(Table Per Concreate Type)
除了資料映射到各自的資料表之外，衍生類別的資料表中還會包含基底類別的欄位
透過FluentAPI設定Map即可
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Data.Entity;

    public class DemoContext : DbContext
    {
        public DbSet&lt;Table1&gt; Table1 { get; set; }
        public DbSet&lt;Table2&gt; Table2 { get; set; }

        protected override void OnModelCreating(DbModelBuilder modelBuilder)
        {
            modelBuilder.Entity&lt;Table1&gt;()
                .Map(x =&gt;
                {
                    x.ToTable("Table1");
                })
                .Map&lt;Table2&gt;(x =&gt;
                {
                    x.ToTable("Table2");
                    x.MapInheritedProperties();
                });
        }
    }
}
</pre></div>
TPC資料表建立的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-O9CIdgHCnZE/VHVN40YQv5I/AAAAAAAAByk/8kwydnaJVQs/s1600/06.TPC%E8%B3%87%E6%96%99%E8%A1%A8%E7%9A%84%E6%A8%A3%E5%AD%90.png)](http://4.bp.blogspot.com/-O9CIdgHCnZE/VHVN40YQv5I/AAAAAAAAByk/8kwydnaJVQs/s1600/06.TPC%E8%B3%87%E6%96%99%E8%A1%A8%E7%9A%84%E6%A8%A3%E5%AD%90.png)</div>
TPC資料儲存的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/--SlDXD6iT3I/VHVN8Rig40I/AAAAAAAABys/G18HVlKXi-Y/s1600/07.TPC%E8%B3%87%E6%96%99%E5%84%B2%E5%AD%98%E7%9A%84%E6%A8%A3%E5%AD%90.png)](http://1.bp.blogspot.com/--SlDXD6iT3I/VHVN8Rig40I/AAAAAAAABys/G18HVlKXi-Y/s1600/07.TPC%E8%B3%87%E6%96%99%E5%84%B2%E5%AD%98%E7%9A%84%E6%A8%A3%E5%AD%90.png)</div>