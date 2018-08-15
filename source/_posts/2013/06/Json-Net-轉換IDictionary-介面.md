---
title: Json.Net 轉換IDictionary 介面
tags:
  - 'C#'
  - JSON
date: 2013-06-27 16:41:00
---

<div>Json.Net 處理 IDictionary介面的方式，會解析成物件的key和value
以下是一個簡單的例子</div>
<div><pre class="brush:csharp">// 淮備資料
Dictionary&lt;string, string&gt; dict1 = new Dictionary&lt;string, string&gt;()
{
    {"a", "1"},
    {"b", "2"},
    {"c", "3"},
};

// 序列化
string jsonString = JsonConvert.SerializeObject(dict1);
Console.WriteLine(jsonString);

// 反序列化
Dictionary&lt;string, string&gt; dict2 = JsonConvert.DeserializeObject&lt;Dictionary&lt;string, string&gt;&gt;(jsonString);
foreach (KeyValuePair&lt;string, string&gt; item in dict2)
{
    Console.WriteLine("key:{0}, value:{1}", item.Key, item.Value);
}

Console.ReadLine();
</pre></div>
<div>執行結果 </div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-h5nzls3rDTc/Ucv6pJBEAxI/AAAAAAAAAx0/f7AO1gRmd9w/s1600/06.png)](http://4.bp.blogspot.com/-h5nzls3rDTc/Ucv6pJBEAxI/AAAAAAAAAx0/f7AO1gRmd9w/s1600/06.png)</div>