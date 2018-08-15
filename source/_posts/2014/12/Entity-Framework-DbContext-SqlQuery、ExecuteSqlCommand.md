---
title: Entity Framework DbContext SqlQuery、ExecuteSqlCommand
tags:
  - DbContext
  - Entity Framework
date: 2014-12-18 16:17:00
---

SqlQuery會回傳結果集，ExecuteSqlCommand會回傳受影響的筆數
傳遞參數的方式有以下幾種
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System.Data;
    using System.Data.Entity;
    using System.Data.SqlClient;

    class Program
    {
        static void Main(string[] args)
        {
            Database.SetInitializer(new DropCreateDatabaseAlways&lt;DemoContext&gt;());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                int colA = 123;
                string colB = "abc";

                // 使用佔位符號
                db.Database.SqlQuery&lt;TableName&gt;("SELECT * FROM TableName WHERE ColA={0} AND ColB={1}", colA, colB);

                // 使用固定名稱的參數
                db.Database.SqlQuery&lt;TableName&gt;("SELECT * FROM TableName WHERE ColA=@P0 AND ColB=@P1", colA, colB);

                // 使用SQL參數
                db.Database.SqlQuery&lt;TableName&gt;(
                    "SELECT * FROM TableName WHERE ColA=@ColA AND ColB=@ColB",
                    new SqlParameter("ColA", colA),
                    new SqlParameter("ColB", colB));

                // 使用SQL參數並明確指定資料形態
                db.Database.SqlQuery&lt;TableName&gt;(
                    "SELECT * FROM TableName WHERE ColA=@ColA AND ColB=@ColB",
                    new SqlParameter("ColA", SqlDbType.Int) { Value = colA },
                    new SqlParameter("ColB", SqlDbType.VarChar, 50) { Value = colB });
            }
        }
    }
}
</pre></div>