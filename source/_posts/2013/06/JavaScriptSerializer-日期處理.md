---
title: JavaScriptSerializer 日期處理
tags:
  - 'C#'
  - JSON
date: 2013-06-19 17:20:00
---

<div>使用JavaScriptSerializer序列化日期時，格式會長的像\/Date(ticks)\/這個樣子
其中的tick為1970/1/1到目前為止的毫秒數
因為沒有時區資訊，而且預設會轉換成UTC時間
所以反序列化回來的時後，會有時區的問題</div><div><pre class="brush:csharp">string jsonString = string.Empty;
DateTime d1 = DateTime.Now;

JavaScriptSerializer jss = new JavaScriptSerializer();
jsonString = jss.Serialize(d1);
Console.WriteLine(jsonString);

DateTime d2 = jss.Deserialize&lt;DateTime&gt;(jsonString);
Console.WriteLine("d1:{0}, kind:{1}", d1, d1.Kind);
Console.WriteLine("d2:{0}, kind:{1}", d2, d2.Kind);
Console.ReadLine();</pre></div><div>執行結果如下 </div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-F8fcPVk1keE/UcFuKhJJOmI/AAAAAAAAAug/KVQeon93Nxw/s1600/01.r1.png)](http://4.bp.blogspot.com/-F8fcPVk1keE/UcFuKhJJOmI/AAAAAAAAAug/KVQeon93Nxw/s1600/01.r1.png)</div><div>解決方法很簡單，反序列化回來的時後，記得把時間ToLocalTime就好了 </div><div><pre class="brush:csharp">string jsonString = string.Empty;
DateTime d1 = DateTime.Now;

JavaScriptSerializer jss = new JavaScriptSerializer();
jsonString = jss.Serialize(d1);
Console.WriteLine(jsonString);

DateTime d2 = jss.Deserialize&lt;DateTime&gt;(jsonString).ToLocalTime();
Console.WriteLine("d1:{0}, kind:{1}", d1, d1.Kind);
Console.WriteLine("d2:{0}, kind:{1}", d2, d2.Kind);
Console.ReadLine();
</pre></div><div>執行結果如下 </div>
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-4i59tTlZwkQ/UcFu8u1O6fI/AAAAAAAAAuo/dy_4uxVg2UY/s1600/01.r2.png)&nbsp;](http://1.bp.blogspot.com/-4i59tTlZwkQ/UcFu8u1O6fI/AAAAAAAAAuo/dy_4uxVg2UY/s1600/01.r2.png)</div><div>另外一個問題是傳到JavaScript的時後，只會把這樣的格式當成字串，需要自行拆解
打開一個Chrome的主控台來測試一下，輸入以下幾行指令</div><div><pre class="brush:javascript">// 建立一個JSON格式的資料
data = { "today": "\/Date(1371631612818)\/" };

// 看一下資料解析的樣子
data.today;

// 把前後的斜線去掉的樣子
data.today.replace(/\//g, "");

// 使用eval來得到日期
eval("new " + data.today.replace(/\//g, ""))

// 使用reg取出ticks的部份
data.today.replace(/\/Date\((\d+)\)\//g, "$1");

// parseInt轉成數字後也能得到日期
new Date(parseInt(data.today.replace(/\/Date\((\d+)\)\//g, "$1")))</pre></div><div>執行結果如下
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-8kc7pENjgFo/UcF2_-0zwkI/AAAAAAAAAu4/iC1ITkH7wGY/s1600/01r3.png)](http://2.bp.blogspot.com/-8kc7pENjgFo/UcF2_-0zwkI/AAAAAAAAAu4/iC1ITkH7wGY/s1600/01r3.png)</div></div>