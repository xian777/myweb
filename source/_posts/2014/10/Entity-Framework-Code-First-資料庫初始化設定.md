---
title: Entity Framework Code First 資料庫初始化設定
tags:
  - Code First
  - Entity Framework
date: 2014-10-31 17:32:00
---

在參考了entityFramework套件之後，設定檔中會自動增加一個EntityFramework的區域設定
其中的defaultConnectionFactory宣告了預設的資料庫位置
不同的版本預設的localdb實體名稱會有不同，這邊的例子是mssqllocaldb
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;configuration&gt;
    &lt;configSections&gt;
        &lt;!-- For more information on Entity Framework configuration, visit http://go.microsoft.com/fwlink/?LinkID=237468 --&gt;
        &lt;section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" /&gt;
    &lt;/configSections&gt;
    &lt;startup&gt;
        &lt;supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" /&gt;
    &lt;/startup&gt;
    &lt;entityFramework&gt;
        &lt;defaultConnectionFactory type="System.Data.Entity.Infrastructure.LocalDbConnectionFactory, EntityFramework"&gt;
            &lt;parameters&gt;
                &lt;parameter value="mssqllocaldb" /&gt;
            &lt;/parameters&gt;
        &lt;/defaultConnectionFactory&gt;
        &lt;providers&gt;
            &lt;provider invariantName="System.Data.SqlClient" type="System.Data.Entity.SqlServer.SqlProviderServices, EntityFramework.SqlServer" /&gt;
        &lt;/providers&gt;
    &lt;/entityFramework&gt;
&lt;/configuration&gt;
</pre></div>
就會自動建立一個包含完整Assembly名稱的資料庫
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-u6i3p3OnimM/VFNEtuySOlI/AAAAAAAABtk/lDxVN9zSfD8/s1600/db.png)](http://3.bp.blogspot.com/-u6i3p3OnimM/VFNEtuySOlI/AAAAAAAABtk/lDxVN9zSfD8/s1600/db.png)</div>

如果在設定檔的連線區段中，有一個和DbContext同名的設定值，就會改用這邊的連線設定
建立的資料庫也會是連線字串中指定的名稱
<div><pre class="brush:xml">&lt;connectionStrings&gt;
    &lt;add name="DemoContext" providerName="System.Data.SqlClient"
            connectionString="Data Source=(localdb)\v11.0;Initial Catalog=Demo;Integrated Security=true;"/&gt;
&lt;/connectionStrings&gt;</pre></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-B1iIDWV-srg/VFNGwAUTTXI/AAAAAAAABt4/eI2Gmbx2deY/s1600/02.%E9%80%A3%E7%B7%9A%E5%AD%97%E4%B8%B2.png)](http://2.bp.blogspot.com/-B1iIDWV-srg/VFNGwAUTTXI/AAAAAAAABt4/eI2Gmbx2deY/s1600/02.%E9%80%A3%E7%B7%9A%E5%AD%97%E4%B8%B2.png)</div>
也可以透過預設建構式指定要使用設定檔中的那個值
<div><pre class="brush:xml">&lt;connectionStrings&gt;
    &lt;add name="DemoContext" providerName="System.Data.SqlClient"
            connectionString="Data Source=(localdb)\v11.0;Initial Catalog=Demo;Integrated Security=true;"/&gt;
    &lt;add name="d1" providerName="System.Data.SqlClient"
            connectionString="Data Source=(localdb)\v11.0;Initial Catalog=d1;Integrated Security=true;"/&gt;
&lt;/connectionStrings&gt;
</pre></div>
<div><pre class="brush:csharp">public class DemoContext : DbContext
{
    public DemoContext() : base("name=d1")
    {
    }

    public DbSet&lt;Class1&gt; Class1 { get; set; }
}
</pre></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-dbjwZcEhoYw/VFNJwZsdzMI/AAAAAAAABuY/Vret3Kef1e0/s1600/d1.png)](http://1.bp.blogspot.com/-dbjwZcEhoYw/VFNJwZsdzMI/AAAAAAAABuY/Vret3Kef1e0/s1600/d1.png)</div>
或是使用DbContext物件時，透過建構式傳入要使用的名稱
<div><pre class="brush:xml">&lt;connectionStrings&gt;
    &lt;add name="DemoContext" providerName="System.Data.SqlClient"
            connectionString="Data Source=(localdb)\v11.0;Initial Catalog=Demo;Integrated Security=true;"/&gt;
    &lt;add name="d1" providerName="System.Data.SqlClient"
            connectionString="Data Source=(localdb)\v11.0;Initial Catalog=d1;Integrated Security=true;"/&gt;
    &lt;add name="d2" providerName="System.Data.SqlClient"
                connectionString="Data Source=(localdb)\v11.0;Initial Catalog=d2;Integrated Security=true;"/&gt;
&lt;/connectionStrings&gt;</pre></div>
<div><pre class="brush:csharp">public class DemoContext : DbContext
{
    public DemoContext() : base("name=d1")
    {
    }

    public DemoContext(string name) : base(name)
    {
    }

    public DbSet&lt;Class1&gt; Class1 { get; set; }
}</pre></div>
<div><pre class="brush:csharp">static void Main(string[] args)
{
    using (DemoContext db = new DemoContext("d2"))
    {
        db.Database.Initialize(true);
    }
}</pre></div>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-BhpDZY3FCIc/VFNLSgDVLuI/AAAAAAAABuk/GA9qeZJMc00/s1600/d2.png)](http://3.bp.blogspot.com/-BhpDZY3FCIc/VFNLSgDVLuI/AAAAAAAABuk/GA9qeZJMc00/s1600/d2.png)</div>
另一種建構式是傳入DbConnection物件，搭配contextOwnsConnection來決定是否要共用連線
<div><pre class="brush:csharp">public class DemoContext : DbContext
{
    public DemoContext() : base("name=d1")
    {
    }

    public DemoContext(string name) : base(name)
    {
    }

    public DemoContext(DbConnection connection) : base(connection, contextOwnsConnection: false)
    {
    }

    public DbSet&lt;Class1&gt; Class1 { get; set; }
}
</pre></div>
如果共用連線的話，在第一個DbContext執行完後就會釋放連線
執行第二個DbContext物件的時後就會報錯
<div><pre class="brush:csharp">static void Main(string[] args)
{
    SqlConnection conn = new SqlConnection(ConfigurationManager.ConnectionStrings["d1"].ConnectionString);

    using (DemoContext db = new DemoContext(conn))
    {
        Console.WriteLine(db.Class1.Count());
    }

    using (DemoContext db = new DemoContext(conn))
    {
        Console.WriteLine(db.Class1.Count());
    }
}
</pre></div>
System.Data.Entity.Database.SetInitializer函式可以用來初始化資料庫
System.Data.Entity.CreateDatabaseIfNotExists
只有在資料庫不存在的時後才會建立，這是預設的策略

System.Data.Entity.DropCreateDatabaseIfModelChanges
只有當資料庫結構發生變化的時後，才砍掉重練

System.Data.Entity.DropCreateDatabaseAlways
不管資料庫結構是否有改變，每次都砍掉重練

通常在應用程式的進入點例如Global.asax，Main會設置初始化策略
但是在切換環境的時後，要改變策略就要重新修改編譯部署
所以比較方便的方式，是配置在設定檔中，有兩種設定方式

一種是設定在AppSetting區段，設成Disabled就是禁用資料庫初始化功能
<div><pre class="brush:csharp">&lt;appSettings&gt;
    &lt;add key="DatabaseInitializerForType ConsoleApplication1.Models.DemoContext, ConsoleApplication1"
            value="System.Data.Entity.DropCreateDatabaseIfModelChanges`1[[ConsoleApplication1.Models.DemoContext, ConsoleApplication1]], EntityFramework" /&gt;
    &lt;!--&lt;add key="DatabaseInitializerForType ConsoleApplication1.Models.DemoContext, ConsoleApplication1"
            value="Disabled" /&gt;--&gt;
&lt;/appSettings&gt;
</pre></div>
一種是設定在entityFramework的contextx區段
<div><pre class="brush:xml">&lt;entityFramework&gt;
    &lt;defaultConnectionFactory type="System.Data.Entity.Infrastructure.LocalDbConnectionFactory, EntityFramework"&gt;
        &lt;parameters&gt;
            &lt;parameter value="mssqllocaldb" /&gt;
        &lt;/parameters&gt;
    &lt;/defaultConnectionFactory&gt;
    &lt;contexts&gt;
        &lt;context type="ConsoleApplication1.Models.DemoContext, ConsoleApplication1"&gt;
            &lt;databaseInitializer type="System.Data.Entity.DropCreateDatabaseIfModelChanges`1[[ConsoleApplication1.Models.DemoContext, ConsoleApplication1]], EntityFramework" /&gt;
        &lt;/context&gt;
    &lt;/contexts&gt;
    &lt;providers&gt;
        &lt;provider invariantName="System.Data.SqlClient" type="System.Data.Entity.SqlServer.SqlProviderServices, EntityFramework.SqlServer" /&gt;
    &lt;/providers&gt;
&lt;/entityFramework&gt;<div>
</div>
</pre></div>
最後可以新增一個自訂的策略，並覆寫Seed函式，就能在初始化資料庫的時後，執行自訂的動作，例如新增資料
<div><pre class="brush:csharp">public class MyInitialize : DropCreateDatabaseIfModelChanges&lt;DemoContext&gt;
{
    protected override void Seed(DemoContext context)
    {
        context.Class1.Add(new Class1 { C1 = "a" });
        context.Class1.Add(new Class1 { C1 = "b" });
        context.Class1.Add(new Class1 { C1 = "c" });
    }
}
</pre></div>