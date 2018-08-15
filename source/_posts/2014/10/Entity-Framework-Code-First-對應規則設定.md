---
title: Entity Framework Code First 對應規則設定
tags:
  - Code First
  - Entity Framework
date: 2014-10-27 17:47:00
---

要改變預設對應規則，可以用兩種方式
一種是使用Attributes的方式，例如[key]
一種是覆寫DbContext的OnModelCreating，透過DbModelBuilder使用Fluent API方式來設定

資料表名稱和主索引
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    public int id { get; set; }
}

public class DemoContext : DbContext
{
    public DbSet&lt;Table1&gt; Table1 { get; set; }

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
        modelBuilder.Entity&lt;Table1&gt;().ToTable("Table1").HasKey(x =&gt; x.id);
    }
}
</pre></div>
自動編號
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    public int id { get; set; }
}

public class DemoContext : DbContext
{
    public DbSet&lt;Table1&gt; Table1 { get; set; }

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
        modelBuilder.Entity&lt;Table1&gt;().ToTable("Table1").HasKey(x =&gt; x.id);
        modelBuilder.Entity&lt;Table1&gt;().Property(x =&gt; x.id)
            .HasDatabaseGeneratedOption(DatabaseGeneratedOption.Identity);
    }
}</pre></div><div>欄位名稱 </div><div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    [Column("sid")]
    public int id { get; set; }
}

public class DemoContext : DbContext
{
    public DbSet&lt;Table1&gt; Table1 { get; set; }

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
        modelBuilder.Entity&lt;Table1&gt;().ToTable("Table1").HasKey(x =&gt; x.id);
        modelBuilder.Entity&lt;Table1&gt;().Property(x =&gt; x.id)
            .HasDatabaseGeneratedOption(DatabaseGeneratedOption.Identity)
            .HasColumnName("sid");
    }
}
</pre></div>
欄位型態
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    [Column("sid", TypeName = "bigint")]
    public int id { get; set; }
}

public class DemoContext : DbContext
{
    public DbSet&lt;Table1&gt; Table1 { get; set; }

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
        modelBuilder.Entity&lt;Table1&gt;().ToTable("Table1").HasKey(x =&gt; x.id);
        modelBuilder.Entity&lt;Table1&gt;().Property(x =&gt; x.id)
            .HasDatabaseGeneratedOption(DatabaseGeneratedOption.Identity)
            .HasColumnName("sid")
            .HasColumnType("bigint");
    }
}
</pre></div>
不可為空(文字)
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    [Column("sid", TypeName = "bigint")]
    public int id { get; set; }

    [Required]
    public string s1 { get; set; }
}

public class DemoContext : DbContext
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
            .IsRequired();
    }
}
</pre></div>
最大長度(文字)
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    [Column("sid", TypeName = "bigint")]
    public int id { get; set; }

    [Required]
    [MaxLength(10)]
    public string s1 { get; set; }
}

public class DemoContext : DbContext
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
            .HasMaxLength(10);
    }
}
</pre></div>
varchar, char(文字)
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    [Column("sid", TypeName = "bigint")]
    public int id { get; set; }

    [Required]
    [MaxLength(10)]
    [Column(TypeName="char")]
    public string s1 { get; set; }
}

public class DemoContext : DbContext
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
    }
}</pre></div>
精準度(浮點數)
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    [Column("sid", TypeName = "bigint")]
    public int id { get; set; }

    [Required]
    [MaxLength(10)]
    [Column(TypeName="char")]
    public string s1 { get; set; }

    public decimal c1 { get; set; }
}

public class DemoContext : DbContext
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
    }
}</pre></div>
時間戳記
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    [Column("sid", TypeName = "bigint")]
    public int id { get; set; }

    [Required]
    [MaxLength(10)]
    [Column(TypeName = "char")]
    public string s1 { get; set; }

    public decimal c1 { get; set; }

    [Timestamp]
    public byte[] t1 { get; set; }
}

public class DemoContext : DbContext
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
}</pre></div>
複合索引
<div><pre class="brush:csharp">[Table("Table1")]
public class Table1
{
    [Key]
    [Column(Order = 1)]
    public int id1 { get; set; }

    [Key]
    [Column(Order = 2)]
    public int id2 { get; set; }
}

public class DemoContext : DbContext
{
    public DbSet&lt;Table1&gt; Table1 { get; set; }

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
        modelBuilder.Entity&lt;Table1&gt;().ToTable("Table1").HasKey(x =&gt; new { x.id1, x.id2 });
    }
}</pre></div>