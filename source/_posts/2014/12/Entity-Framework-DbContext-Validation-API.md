---
title: Entity Framework DbContext Validation API
tags:
  - DbContext
  - Entity Framework
date: 2014-12-18 15:46:00
---

先建一張資料表，並加上幾個Attribute當例子
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System;
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Table1")]
    public class Table1
    {
        [Key]
        public int Table1Id { get; set; }

        [Required]
        [StringLength(10, MinimumLength = 2)]
        public string C1 { get; set; }

        [Range(10, 20)]
        public int C2 { get; set; }

        public DateTime D1 { get; set; }

        public DateTime D2 { get; set; }
    }
}
</pre></div>
針對屬性驗證
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;

    class Program
    {
        static void Main(string[] args)
        {
            Database.SetInitializer(new DropCreateDatabaseAlways&lt;DemoContext&gt;());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                Table1 table1 = new Table1
                {
                    C1 = "a",
                    C2 = 1,
                    D1 = DateTime.Now,
                    D2 = DateTime.Now.AddDays(-1)
                };

                foreach (var item in db.Entry(table1).Property(x =&gt; x.C1).GetValidationErrors())
                {
                    Console.WriteLine(item.ErrorMessage);
                }

                foreach (var item in db.Entry(table1).Property(x =&gt; x.C2).GetValidationErrors())
                {
                    Console.WriteLine(item.ErrorMessage);
                }
            }
        }
    }
}
</pre></div>
針對實體驗證
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;

    class Program
    {
        static void Main(string[] args)
        {
            Database.SetInitializer(new DropCreateDatabaseAlways&lt;DemoContext&gt;());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                Table1 table1 = new Table1
                {
                    C1 = "a",
                    C2 = 1,
                    D1 = DateTime.Now,
                    D2 = DateTime.Now.AddDays(-1)
                };

                foreach (var item in db.Entry(table1).GetValidationResult().ValidationErrors)
                {
                    Console.WriteLine(item.ErrorMessage);
                }
            }
        }
    }
}
</pre></div>
針對DbContext驗證
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;

    class Program
    {
        static void Main(string[] args)
        {
            Database.SetInitializer(new DropCreateDatabaseAlways&lt;DemoContext&gt;());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                Table1 table1 = new Table1
                {
                    C1 = "a",
                    C2 = 1,
                    D1 = DateTime.Now,
                    D2 = DateTime.Now.AddDays(-1)
                };

                db.Table1.Add(table1);
                foreach (var result in db.GetValidationErrors())
                {
                    foreach (var item in result.ValidationErrors)
                    {
                        Console.WriteLine(item.ErrorMessage);
                    }
                }
            }
        }
    }
}
</pre></div>
輸出的畫面如下
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-609pUnv8j8U/VJJ_9ch4SYI/AAAAAAAAB0U/QV7isgRzPNI/s1600/01.png)](http://3.bp.blogspot.com/-609pUnv8j8U/VJJ_9ch4SYI/AAAAAAAAB0U/QV7isgRzPNI/s1600/01.png)</div>
自定義驗證屬性規則，加入一個靜態類別，用來放自定義的驗證規則
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.ComponentModel.DataAnnotations;

    public static class MyCustomRule
    {
        public static ValidationResult MyStringRule(string value)
        {
            if (value == "a")
            {
                return new ValidationResult("字串不可為a");
            }
            else
            {
                return ValidationResult.Success;
            }
        }

        public static ValidationResult MyIntRule(int value)
        {
            if (value == 1)
            {
                return new ValidationResult("數字不可為1");
            }
            else
            {
                return ValidationResult.Success;
            }
        }
    }
}
</pre></div>
在屬性上加入自定義的驗證規則
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System;
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Table1")]
    public class Table1
    {
        [Key]
        public int Table1Id { get; set; }

        [Required]
        [StringLength(10, MinimumLength = 2)]
        [CustomValidation(typeof(MyCustomRule), "MyStringRule")]
        public string C1 { get; set; }

        [Range(10, 20)]
        [CustomValidation(typeof(MyCustomRule), "MyIntRule")]
        public int C2 { get; set; }

        public DateTime D1 { get; set; }

        public DateTime D2 { get; set; }
    }
}
</pre></div>
驗證資料的時後，就會包含自定義的規則
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-WL8Il-n32Jk/VJKACUZv-DI/AAAAAAAAB0c/XTMlR3RudAY/s1600/02.png)](http://2.bp.blogspot.com/-WL8Il-n32Jk/VJKACUZv-DI/AAAAAAAAB0c/XTMlR3RudAY/s1600/02.png)</div>
自定義驗證實體規則，在實體上實作IValidatableObject介面
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Table1")]
    public class Table1 : IValidatableObject
    {
        [Key]
        public int Table1Id { get; set; }

        [Required]
        // [StringLength(10, MinimumLength = 2)]
        public string C1 { get; set; }

        // [Range(10, 20)]
        public int C2 { get; set; }

        public DateTime D1 { get; set; }

        public DateTime D2 { get; set; }

        public IEnumerable&lt;ValidationResult&gt; Validate(ValidationContext validationContext)
        {
            if (this.C1 == "a")
            {
                yield return new ValidationResult("字串不可為a");
            }

            if (this.C2 == 1)
            {
                yield return new ValidationResult("數字不可為1");
            }

            if (this.D1 &gt;= this.D2)
            {
                yield return new ValidationResult("d1不能大於d2");
            }
        }
    }
}
</pre></div>
自定義驗證DbContext規則，覆寫ValidateEntity函式
<div><pre class="brush:csharp">namespace ConsoleApplication1.Models
{
    using System.Collections.Generic;
    using System.Data.Entity;
    using System.Data.Entity.Infrastructure;
    using System.Data.Entity.Validation;

    public class DemoContext : DbContext
    {
        public DbSet&lt;Table1&gt; Table1 { get; set; }
        public DbSet&lt;Table2&gt; Table2 { get; set; }

        protected override DbEntityValidationResult ValidateEntity(DbEntityEntry entityEntry, IDictionary&lt;object, object&gt; items)
        {
            var result = base.ValidateEntity(entityEntry, items);
            var table1 = entityEntry.Entity as Table1;
            if (table1 != null)
            {
                if (table1.C1 == "a")
                {
                    result.ValidationErrors.Add(new DbValidationError("C1", "字串不可為a"));
                }

                if (table1.C2 == 1)
                {
                    result.ValidationErrors.Add(new DbValidationError("C2", "數字不可為1"));
                }

                if (table1.D1 &gt;= table1.D2)
                {
                    result.ValidationErrors.Add(new DbValidationError("D1", "d1不能大於d2"));
                }
            }

            return result;
        }
    }
}
</pre></div>輸出的結果如下
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-qQ9gSatBC6c/VJKGMywO5NI/AAAAAAAAB0s/rEVP1WCzPyg/s1600/03.png)](http://4.bp.blogspot.com/-qQ9gSatBC6c/VJKGMywO5NI/AAAAAAAAB0s/rEVP1WCzPyg/s1600/03.png)</div>