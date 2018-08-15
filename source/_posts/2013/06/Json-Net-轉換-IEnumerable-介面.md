---
title: Json.Net 轉換 IEnumerable 介面
tags:
  - 'C#'
  - JSON
date: 2013-06-27 16:31:00
---

<div>Json.Net對於IEnumerable介面的處理，同樣是序列化成陣列的格式
首先先宣告個物件以便之後的處理</div>
<div><pre class="brush:csharp">private class Person
{
    public int id { get; set; }
    public string name { get; set; }
    public DateTime date { get; set; }
}
</pre></div>
<div>轉換IEnumerable介面，以List為例 </div><div><pre class="brush:csharp">static void Main(string[] args)
{
    // 淮備資料
    List&lt;Person&gt; list1 = new List&lt;Person&gt;()
    {
        new Person()
        {
            id = 1,
            name = "p1",
            date = DateTime.Today.AddDays(-1)

        },
        new Person()
        {
            id = 2,
            name="p2",
            date = DateTime.Today
        },
        new Person()
        {
            id = 3,
            name = "p3",
            date = DateTime.Today.AddDays(1)
        }
    };

    // 序列化
    string jsonString = JsonConvert.SerializeObject(list1);
    Console.WriteLine(jsonString);

    // 反序列化
    List&lt;Person&gt; list2 = JsonConvert.DeserializeObject&lt;List&lt;Person&gt;&gt;(jsonString);
    foreach (var item in list2)
    {
        Console.WriteLine("id:{0}, name:{1}, date:{2}", item.id, item.name, item.date);
    }

    Console.ReadLine();
}
</pre></div>
<div>執行結果
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-jcrtfBwMruc/Ucv4HcocPmI/AAAAAAAAAxs/PINPmEH-b6g/s1600/05.png)](http://3.bp.blogspot.com/-jcrtfBwMruc/Ucv4HcocPmI/AAAAAAAAAxs/PINPmEH-b6g/s1600/05.png)</div></div>