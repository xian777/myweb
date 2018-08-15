---
title: DataContractJsonSerializer 日期處理
tags:
  - 'C#'
  - JSON
date: 2013-06-20 16:25:00
---

<div>使用DataContractJsonSerializer序列化日期時，格式為\/Date(ticks+時區資料)\/這個樣子
因為有時區資料，所以不用像JavaScriptSerializer一樣還要手動加上ToLocalTime函式</div><div><pre class="brush:csharp">// 初始化DataContractJsonSerializer類別
DateTime d1 = DateTime.Now;
DataContractJsonSerializer dcjs = new DataContractJsonSerializer(typeof(DateTime));
string jsonString = string.Empty;

// 序列化資料
using (MemoryStream ms = new MemoryStream())
{
    dcjs.WriteObject(ms, d1);
    jsonString = Encoding.UTF8.GetString(ms.ToArray());
    Console.WriteLine(jsonString);
    Console.WriteLine();
}

// 反序列化資料
using (MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(jsonString)))
{
    DateTime d2 = (DateTime)dcjs.ReadObject(ms);
    Console.WriteLine("d1:{0}, kind:{1}", d1, d1.Kind);
    Console.WriteLine("d2:{0}, kind:{1}", d2, d2.Kind);
}

Console.ReadLine();
</pre></div>
<div>執行結果 
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-BYDVvul8U9Q/UcK6kL-DMWI/AAAAAAAAAwQ/TbbHuT0BD2A/s1600/04-4.png)](http://1.bp.blogspot.com/-BYDVvul8U9Q/UcK6kL-DMWI/AAAAAAAAAwQ/TbbHuT0BD2A/s1600/04-4.png)</div></div>
<div>使用JavaScript處理的時後，因為多了時區資料，所以reg要修改一下
打開一個Chrome的主控台並輸入以下幾行指令</div><div><pre class="brush:javascript">// 建立一個JSON格式的資料
data = { "today": "\/Date(1371716206301+0800)\/"};

// 看一下資料解析的樣子
data.today;

// 把前後的斜線去掉的樣子
data.today.replace(/\//g, "");

// 使用eval來得到日期
eval("new " + data.today.replace(/\//g, ""))

// 使用reg取出ticks的部份
data.today.replace(/\/Date\((.*?)\)\//g, "$1");

// parseInt轉成數字後也能得到日期
new Date(parseInt(data.today.replace(/\/Date\((.*?)\)\//g, "$1")))
</pre></div><div>執行結果如下
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-lX5uOGKia5E/UcK8KOlx7nI/AAAAAAAAAwg/uMOO8i9qw-c/s1600/04-5.png)](http://1.bp.blogspot.com/-lX5uOGKia5E/UcK8KOlx7nI/AAAAAAAAAwg/uMOO8i9qw-c/s1600/04-5.png)</div></div>