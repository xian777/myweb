---
title: DataContractJsonSerializer 用法
tags:
  - 'C#'
  - JSON
date: 2013-06-20 15:15:00
---

<div>首先需要先定義資料類別
[DataContract](http://msdn.microsoft.com/zh-tw/library/system.runtime.serialization.datacontractattribute.aspx)用來標記類別
[DataMember](http://msdn.microsoft.com/zh-tw/library/system.runtime.serialization.datamemberattribute.aspx)用來標記屬性，Name可以用來變更序列化後的名稱，Order則是序列化的順序
[IgnoreDataMember](http://msdn.microsoft.com/zh-tw/library/system.runtime.serialization.ignoredatamemberattribute.aspx)用來標記屬性，表示不參與序列化過程</div><div><pre class="brush:csharp">[DataContract]
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
<div>初始化DataContractJsonSerializer類別時，需傳入要序列化的資料型別 </div><div><pre class="brush:csharp">// 淮備序列化的類別資料
JsonData d1 = new JsonData()
{
    Id = 1,
    Name = "data",
    Today = DateTime.Now,
    IsBool = true,
    UnlessField = "沒用到的欄位"
};

// 初始化DataContractJsonSerializer類別
DataContractJsonSerializer dcjs = new DataContractJsonSerializer(typeof(JsonData));
string jsonString = string.Empty;
</pre></div>
<div>序列化資料使用WriteObject寫入Stream
再用Encoding取得json字串 </div><div><pre class="brush:csharp">// 序列化資料
using (MemoryStream ms = new MemoryStream())
{
    dcjs.WriteObject(ms, d1);
    jsonString = Encoding.UTF8.GetString(ms.ToArray());
    Console.WriteLine(jsonString);
}
</pre></div>
<div>反序列化資料先用Encoding取得取得Byte Array讀入Stream
再用ReadObject讀出資料型別</div><div><pre class="brush:csharp">// 反序列化資料
using (MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(jsonString)))
{
    JsonData d2 = dcjs.ReadObject(ms) as JsonData;
    Console.WriteLine(
        "Id:{0}, Name:{1}, Today:{2}, IsBool:{3}, UnlessField:{4}",
        d2.Id,
        d2.Name,
        d2.Today,
        d2.IsBool,
        d2.UnlessField);
}
</pre></div><div>
執行結果如下
1\. 日期的部份加入了時區的資料，所以反序列化回來後不用再手動加上ToLocalTime函數
2.&nbsp; 標記為IgnoreDataMember的欄位並沒有參考序列化的過程，反序列化回來後是空字串
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-eBsCYgXxTuk/UcKrNqc_bBI/AAAAAAAAAvg/4fo00gDjWwA/s1600/04.1.png)](http://4.bp.blogspot.com/-eBsCYgXxTuk/UcKrNqc_bBI/AAAAAAAAAvg/4fo00gDjWwA/s1600/04.1.png)</div></div>