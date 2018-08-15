---
title: DataContractJsonSerializer 轉換 IDictionary 介面
tags:
  - 'C#'
  - JSON
date: 2013-06-20 15:50:00
---

<div>轉換IDictionary介面的方式也一樣，只要注意初始化DataContractJsonSerializer類別時傳入IDictionary介面就好
但是輸出的結果並不如預期中為物件的格式
直接宣告一個Dictionary來當範例</div><div><pre class="brush:csharp">// 淮備序列化的類別資料
Dictionary&lt;int, object&gt; dataList = new Dictionary&lt;int, object&gt;()
{
    {1, "a"},
    {2, "b"},
    {3, "c"}
};
</pre></div><div>
初始化時要傳入這個Dictionary的型別 </div><div><pre class="brush:csharp">// 初始化DataContractJsonSerializer類別
DataContractJsonSerializer dcjs = new DataContractJsonSerializer(typeof(Dictionary&lt;int, object&gt;));
string jsonString = string.Empty;
</pre></div>
<div>序列化的方式一樣 </div><div><pre class="brush:csharp">// 序列化資料
using (MemoryStream ms = new MemoryStream())
{
    dcjs.WriteObject(ms, dataList);
    jsonString = Encoding.UTF8.GetString(ms.ToArray());
    Console.WriteLine(jsonString);
    Console.WriteLine();
}
</pre></div>
<div>反序列化的方式也一樣 </div><div><pre class="brush:csharp">// 反序列化資料
using (MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(jsonString)))
{
    Dictionary&lt;int, object&gt; data2List = dcjs.ReadObject(ms) as Dictionary&lt;int, object&gt;;
    foreach (KeyValuePair&lt;int, object&gt; item in data2List)
    {
        Console.WriteLine(
            "Key:{0}, Value:{1}",
            item.Key,
            item.Value);
    }
}
</pre></div>
<div>執行結果可以看到序列化成JSON字串時，會固定變成Key:xx, Value:oo的陣列
這在不同JSON元件之間的轉換會造成一些問題
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-Et1ueQR5Ln0/UcKzdBLQPvI/AAAAAAAAAwA/lxpN84Etqmk/s1600/04-3.png)](http://1.bp.blogspot.com/-Et1ueQR5Ln0/UcKzdBLQPvI/AAAAAAAAAwA/lxpN84Etqmk/s1600/04-3.png)</div></div>