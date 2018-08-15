---
title: Entity Framework Code First 預設對應規則
tags:
  - Code First
  - Entity Framework
date: 2014-10-20 15:43:00
---

資料庫
預設採用SQLEXPRESS，如果沒有SQLEXPRESS執行個體，會嘗試Localdb
如果有和DbContext同名的連線字串，就會直接使用
也可透過覆寫建構式的時後，傳入指定的連線字串名稱
或是透過DbConnection，在執行階段傳入連線物件

Table
資料表為類別名稱的複數形式，而且schema都為dbo
可以透過System.ComponentModel.DataAnnotations.Schema.Table
或是Fluent API的Entity&lt;T&gt;.ToTable來指定資料表的名稱
也可以覆寫OnModelCreating，移除複數資料表的約定
modelBuilder.Conventions.Remove&lt;PluralizingTableNameConvention&gt;();

主索引
預設為類別名稱加上Id結尾的屬性，如果資料形態是int，還會加上自動編號
可以透過System.ComponentModel.DataAnnotations.Key
或是Fluent API的Entity&lt;T&gt;.HasKey來指定
如果是複合索引，Attribute方式需再加上Column來指定欄位的順序
Fluent API則是傳入一個匿名型別

外部索引
如果類別之間有一對多的關系，會自動生成Foreign Key
欄位名稱是導覽屬性加上底線再加上對應主索引的欄位名稱
可以透過System.ComponentModel.DataAnnotations.Schema.ForeignKey來指定
或是透過Fluent API的Entity&lt;T&gt;.Hasxxx().Withxxx來指定
xxx可以是Optional(0或多個)、Required(1或多個)、Many(多個)

資料型態
實值型別會是not null
參考型別會是null
nullable型別會是null
可以透過System.ComponentModel.DataAnnotations.Required來設定不可空值
或是透過Fluent API的Entity&lt;T&gt;().IsRequired()來指定不可空值，IsOptional指定可以空值

也可以透過System.ComponentModel.DataAnnotations.Schema.Column來明確指定對應的格式
或是透過Fluent API的Entity&lt;T&gt;().Property().HasColumnType來指定對應的格式
或是IsUnicode來指定是否為Unicode

<div><table border="1" style="width: 100%px;"><tbody><tr><td width=":50%">C#</td><td width=":50%">SQL Server</td><td>nullable</td></tr><tr><td>byte</td><td>tinyint</td><td>NOT NULL</td></tr><tr><td>short</td><td>smallint</td><td>NOT NULL</td></tr><tr><td>int</td><td>int</td><td>NOT NULL</td></tr><tr><td>long</td><td>bigint</td><td>NOT NULL</td></tr><tr><td>float</td><td>real</td><td>NOT NULL</td></tr><tr><td>double</td><td>float</td><td>NOT NULL</td></tr><tr><td>decimal</td><td>decimal(18,2)</td><td>NOT NULL</td></tr><tr><td>string</td><td>nvarchar(max)</td><td>NULL</td></tr><tr><td>byte[]</td><td>varbinary(max)</td><td>NOT NULL</td></tr><tr><td>bool</td><td>bit</td><td>NOT NULL</td></tr><tr><td>datetime</td><td>datetime</td><td>NOT NULL</td></tr></tbody></table></div>