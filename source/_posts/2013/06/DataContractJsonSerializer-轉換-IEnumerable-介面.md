---
title: DataContractJsonSerializer 轉換 IEnumerable 介面
tags:
  - 'C#'
  - JSON
date: 2013-06-20 15:34:00
---

<div>轉換IEnumerable的用法和一般的資料沒什麼不同
差別只在於初始化類別的時後，傳入的資料型別也要改成IEnumerable
宣告一個相同的資料型別來做範例 </div><div><pre class="brush:csharp">[DataContract]
public class JsonData
{
    [DataMember(Name = "ID", Order = 0)]
    public int Id { get; set; }

    [DataMember(Order = 1)]
    public string Name { get; set; }

    [DataMember(Order = 2)]
    public DateTime Today { get; set; }

    [DataMember(Order=3)]
    public bool IsBool { get; set; }

    [IgnoreDataMember()]
    public string UnlessField { get; set; }
}
</pre></div>
<div>準備一個List來當做序列化的資料
初始化DataContractJsonSerializer類別的時後，也要傳入這個List的型別</div><div><pre class="brush:csharp">// 淮備序列化的類別資料
List&lt;JsonData&gt; dataList = new List&lt;JsonData&gt;()
{
    new JsonData()
    {
        Id = 1,
        Name = "data1",
        Today = DateTime.Now.AddDays(-1),
        IsBool = true,
        UnlessField = "沒用到的欄位1"
    },
    new JsonData()
    {
        Id = 2,
        Name = "data2",
        Today = DateTime.Now,
        IsBool = false,
        UnlessField = "沒用到的欄位2"
    },
    new JsonData()
    {
        Id = 3,
        Name = "data3",
        Today = DateTime.Now.AddDays(1),
        IsBool = true,
        UnlessField = "沒用到的欄位3"
    }

};

// 初始化DataContractJsonSerializer類別
DataContractJsonSerializer dcjs = new DataContractJsonSerializer(typeof(List&lt;JsonData&gt;));
string jsonString = string.Empty;
</pre></div>
<div>序列化的方法一樣 </div><div><pre class="brush:csharp">// 序列化資料
using (MemoryStream ms = new MemoryStream())
{
    dcjs.WriteObject(ms, dataList);
    jsonString = Encoding.UTF8.GetString(ms.ToArray());
    Console.WriteLine(jsonString);
    Console.WriteLine();
}
</pre></div>
<div>反序列化的方法也一樣 </div><div><pre class="brush:csharp">// 反序列化資料
using (MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(jsonString)))
{
    List&lt;JsonData&gt; data2List = dcjs.ReadObject(ms) as List&lt;JsonData&gt;;
    foreach (JsonData item in data2List)
    {
        Console.WriteLine(
            "Id:{0}, Name:{1}, Today:{2}, IsBool:{3}, UnlessField:{4}",
            item.Id,
            item.Name,
            item.Today,
            item.IsBool,
            item.UnlessField);
    }
}
</pre></div>
<div>執行結果資料一樣序列化成陣列的樣子，反序列化也沒什麼問題 
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-j1sVYW0xrmk/UcKv_7wCK4I/AAAAAAAAAvw/gpDughnVeRg/s1600/04.2.png)](http://4.bp.blogspot.com/-j1sVYW0xrmk/UcKv_7wCK4I/AAAAAAAAAvw/gpDughnVeRg/s1600/04.2.png)</div></div>