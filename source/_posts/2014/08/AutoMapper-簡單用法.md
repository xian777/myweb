---
title: AutoMapper 簡單用法
tags:
  - AutoMapper
date: 2014-08-05 17:06:00
---

<div>AutoMapper是一個用來處理類別之間轉換的套件，以下用個Model和ViewModel的轉換當例子

首先是一個簡單的Model</div><div><pre class="brush:csharp">public class DemoModel
{
    public int Id { get; set; }
    public string Name { get; set; }
}
</pre></div><div>
再來是對應的ViewModel</div><div><pre class="brush:csharp">public class DemoViewModel
{
    public int Id { get; set; }
    public string Name { get; set; }
}
</pre></div><div>
兩個類別要轉換的一般寫法</div><div><pre class="brush:csharp">private static void V1()
{
    DemoModel c1 = new DemoModel()
    {
        Id = 123,
        Name = "abc"
    };

    DemoViewModel c2 = new DemoViewModel
    {
        Id = c1.Id,
        Name = c1.Name
    };

    Console.WriteLine("id:{0}, name:{1}", c2.Id, c2.Name);
}
</pre></div><div>
使用AutoMapper之後的寫法</div><div><pre class="brush:csharp">private static void V2()
{
    Mapper.CreateMap&lt;DemoModel, DemoViewModel&gt;();
    DemoModel c1 = new DemoModel
    {
        Id = 123,
        Name = "abc"
    };

    DemoViewModel c2 = Mapper.Map&lt;DemoModel, DemoViewModel&gt;(c1);
    Console.WriteLine("id:{0}, name:{1}", c2.Id, c2.Name);
}</pre></div>
<div>AutoMapper用來把DataReader轉成IEnumerable也很簡單，以北風資料庫的Customers為例子</div><div>首先是轉換後的CustViewModel</div><div><pre class="brush:csharp">public class CustViewModel
{
    public int CustomerID { get; set; }
    public string CompanyName { get; set; }
    public string City { get; set; }
    public string Region { get; set; }
    public string PostalCode { get; set; }
    public string Country { get; set; }
    public string Phone { get; set; }
    public string Fax { get; set; }
}</pre></div>
<div>取得資料列表</div><div><pre class="brush:csharp">public static IEnumerable&lt;CustViewModel&gt; GetList()
{
    Mapper.CreateMap&lt;IDataReader, IEnumerable&lt;CustViewModel&gt;&gt;();
    string connString = @"data source=(localdb)\v11.0; initial catalog=Northwind; trusted_connection=true;";
    using (SqlConnection conn = new SqlConnection(connString))
    {
        SqlCommand cmd = new SqlCommand("select * from customers", conn);
        conn.Open();
        SqlDataReader dtr = cmd.ExecuteReader();
        return Mapper.Map&lt;IDataReader, IEnumerable&lt;CustViewModel&gt;&gt;(dtr);
    }
}</pre></div>