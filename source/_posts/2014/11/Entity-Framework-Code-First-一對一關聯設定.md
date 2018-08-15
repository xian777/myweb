---
title: Entity Framework Code First 一對一關聯設定
tags:
  - Code First
  - Entity Framework
date: 2014-11-24 17:42:00
---

在兩個類別之間，各自包含一個引用屬性，就會被當成一對一關系
只是那張是主資料表，需要利用Fluent API來設定

主資料表
<div><pre class="brush:csharp">using System.ComponentModel.DataAnnotations;

public partial class TableA
{
    [Key]
    public int TabId { get; set; }

    public int C1 { get; set; }

    public virtual TableB TableB { get; set; }
}</pre></div>
對應的資料表
<div><pre class="brush:csharp">using System.ComponentModel.DataAnnotations;

public partial class TableB
{
    [Key]
    public int TabId { get; set; }

    public int CC1 { get; set; }

    public virtual TableA TableA { get; set; }
}</pre></div>
設定關聯
<div><pre class="brush:csharp">using System.Data.Entity;

public partial class DemoContext : DbContext
{
    public DemoContext()
        : base("name=DemoContext")
    {
    }

    public virtual DbSet&lt;TableA&gt; TableA { get; set; }
    public virtual DbSet&lt;TableB&gt; TableB { get; set; }

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
        modelBuilder.Entity&lt;TableA&gt;()
            .HasOptional(x =&gt; x.TableB)
            .WithRequired(x =&gt; x.TableA);
    }
}</pre></div>
建立出一對一關系的資料表
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-rbt4EUaTb5Q/VHL9dejT89I/AAAAAAAABwI/QiNQmRhMIfo/s1600/%E6%9C%AA%E5%91%BD%E5%90%8D.png)](http://2.bp.blogspot.com/-rbt4EUaTb5Q/VHL9dejT89I/AAAAAAAABwI/QiNQmRhMIfo/s1600/%E6%9C%AA%E5%91%BD%E5%90%8D.png)</div>

關聯圖
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-4NfXgZRL470/VHL_AJYWIvI/AAAAAAAABwU/0OA1cJHzG5s/s1600/%E6%9C%AA%E5%91%BD%E5%90%8D.png)](http://3.bp.blogspot.com/-4NfXgZRL470/VHL_AJYWIvI/AAAAAAAABwU/0OA1cJHzG5s/s1600/%E6%9C%AA%E5%91%BD%E5%90%8D.png)</div>