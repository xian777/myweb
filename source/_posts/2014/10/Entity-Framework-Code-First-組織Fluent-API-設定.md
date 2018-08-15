---
title: Entity Framework Code First 組織Fluent API 設定
tags:
  - Code First
  - Entity Framework
date: 2014-10-27 18:16:00
---

Fluent API可以設定的功能比較多，但每一個欄位就要寫一行，越大的專案設定就會越多
<div>可以透過EntityTypeConfiguration&lt;T&gt;來分類</div><div>
一般的設定方式</div><div><pre class="brush:csharp">public class DemoContext : DbContext
{
    public DbSet&lt;Table1&gt; Table1 { get; set; }

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
        modelBuilder.Entity&lt;Table1&gt;().ToTable("Table1").HasKey(x =&gt; x.id);
        modelBuilder.Entity&lt;Table1&gt;().Property(x =&gt; x.id)
            .HasDatabaseGeneratedOption(DatabaseGeneratedOption.Identity)
            .HasColumnName("sid")
            .HasColumnType("bigint");
        modelBuilder.Entity&lt;Table1&gt;().Property(x =&gt; x.s1)
            .IsRequired()
            .HasMaxLength(10)
            .IsFixedLength()
            .IsUnicode(false);
        modelBuilder.Entity&lt;Table1&gt;().Property(x =&gt; x.c1)
            .HasPrecision(18, 2);
        modelBuilder.Entity&lt;Table1&gt;().Property(x =&gt; x.t1)
            .IsRowVersion();
    }
}</pre>
</div><div>分類後的設定方式</div><div><pre class="brush:csharp">public class DemoContext : DbContext
{
    public DbSet&lt;Table1&gt; Table1 { get; set; }

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
        modelBuilder.Configurations.Add(new Table1Configuration());
    }

    private class Table1Configuration : EntityTypeConfiguration&lt;Table1&gt;
    {
        public Table1Configuration()
        {
            this.ToTable("Table1").HasKey(x =&gt; x.id);
            this.Property(x =&gt; x.id)
                .HasDatabaseGeneratedOption(DatabaseGeneratedOption.Identity)
                .HasColumnName("sid")
                .HasColumnType("bigint");
            this.Property(x =&gt; x.s1)
                .IsRequired()
                .HasMaxLength(10)
                .IsFixedLength()
                .IsUnicode(false);
            this.Property(x =&gt; x.c1)
                .HasPrecision(18, 2);
            this.Property(x =&gt; x.t1)
                .IsRowVersion();
        }
    }
}</pre>
</div>