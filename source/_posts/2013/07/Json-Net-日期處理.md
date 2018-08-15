---
title: Json.Net 日期處理
tags:
  - 'C#'
  - JSON
date: 2013-07-01 15:49:00
---

<div>Json.Net 序列化的日期格式，在4.5版之前是Microsoft Date Format:"\/Date(ticks)\/"
4.5版之後，預設的日期格式已經改成[ISO 8601 standard](http://en.wikipedia.org/wiki/ISO_8601)
可以透過JsonSerializerSettings的方式來指定序列化的格式
反序列化的時後會自動識別不需另外指定

另外還有一種JavaScript格式，需要透過指定JavaScriptDateTimeConverter來轉換
反序列化的時後也需要明確指定，否則會出現錯誤</div>
<div><pre class="brush:csharp">DateTime d = DateTime.Now;

Console.WriteLine("datetime:{0}\r\n", d);

// ISO8601的格式
string jsonString1 = JsonConvert.SerializeObject(d);
Console.WriteLine("ISO8601 Date Format:{0}", jsonString1);
DateTime d1 = JsonConvert.DeserializeObject&lt;DateTime&gt;(jsonString1);
Console.WriteLine("datetime:{0}, kind:{1}\r\n", d1, d1.Kind);

// Microsoft Date Format
string jsonString2 = JsonConvert.SerializeObject(
    d, 
    new JsonSerializerSettings() 
    {
        DateFormatHandling = DateFormatHandling.MicrosoftDateFormat 
    });
Console.WriteLine("Microsoft Date Format:{0}", jsonString2);
DateTime d2 = JsonConvert.DeserializeObject&lt;DateTime&gt;(jsonString2);
Console.WriteLine("datetime:{0}, kind:{1}\r\n", d2, d2.Kind);

// JavaScript Date Format
string jsonString3 = JsonConvert.SerializeObject(d, new JavaScriptDateTimeConverter());
Console.WriteLine("JavaScript Date Format:{0}", jsonString3);
DateTime d3 = JsonConvert.DeserializeObject&lt;DateTime&gt;(jsonString3, new JavaScriptDateTimeConverter());
Console.WriteLine("datetime:{0}, kind:{1}\r\n", d3.ToLocalTime(), d3.Kind);

Console.ReadLine();
</pre></div>
<div>執行結果
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-4xQzthsARkg/UdEuL_710dI/AAAAAAAAAyE/AzwYlXttM-s/s1600/01.png)](http://3.bp.blogspot.com/-4xQzthsARkg/UdEuL_710dI/AAAAAAAAAyE/AzwYlXttM-s/s677/01.png)</div></div>
<div>ISO8601格式需要ECMAScript 5才能支援，瀏覽器的版本可以參考[ECMAScript 5 compatibility table](http://kangax.github.io/es5-compat-table/)</div>打開一個Chrome的主控台並輸入以下幾行指令
<div><pre class="brush:javascript">// 建立一個ISO8601格式的日期資料
d = {"today":"2013-07-01T15:21:47.6748196+08:00"};
// 日期會被當成字串
d.today;
// 直接使用new Date得到日期
new Date(d.today)
</pre></div>
<div>執行結果
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-YMXrosU4F44/UdEz_N0kFqI/AAAAAAAAAyU/ufr1TaaN3J0/s1600/02.png)](http://1.bp.blogspot.com/-YMXrosU4F44/UdEz_N0kFqI/AAAAAAAAAyU/ufr1TaaN3J0/s555/02.png)</div></div>