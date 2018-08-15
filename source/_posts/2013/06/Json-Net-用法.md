---
title: Json.Net 用法
tags:
  - 'C#'
  - JSON
date: 2013-06-27 16:02:00
---

<div>首先用最基本的JsonTextWriter和JsonTextReader
JsonTextWriter使用成對的方法來輸出Json字串
JsonTextReader使用Read方法來持續讀取Json字串
看得出來在使用上有點拖泥帶水</div><div><pre class="brush:csharp">static void Main(string[] args)
{
    string jsonString = string.Empty;

    using (StringWriter sw = new StringWriter())
    {
        using (JsonTextWriter writer = new JsonTextWriter(sw))
        {
            // 開始輸出物件
            writer.WriteStartObject();

            // 輸出屬性:id
            writer.WritePropertyName("id");
            writer.WriteValue(1);

            // 輸出屬性:name
            writer.WritePropertyName("name");
            writer.WriteValue("xian");

            // 輸出屬性today
            writer.WritePropertyName("today");
            writer.WriteValue(DateTime.Today);

            // 開始輸出陣列
            writer.WritePropertyName("arraydata");
            writer.WriteStartArray();
            writer.WriteValue(1);
            writer.WriteValue(2);
            writer.WriteValue(3);

            // 結束輸出陣列
            writer.WriteEndArray();

            // 結束串出物件
            writer.WriteEndObject();
        }

        jsonString = sw.ToString();
        Console.WriteLine(jsonString);
    }

    using (StringReader sr = new StringReader(jsonString))
    {
        using (JsonTextReader reader = new JsonTextReader(sr))
        {
            while (reader.Read())
            {
                if (reader.Value != null)
                {
                    Console.WriteLine("token:{0}, value:{1}", reader.TokenType, reader.Value);
                }
                else
                {
                    Console.WriteLine("token:{0}", reader.TokenType);
                }
            }
        }
    }

    Console.ReadLine();
}
</pre></div>
<div>執行結果
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-g8DBrvIgZWI/UcvtZzhR10I/AAAAAAAAAxI/zFqpHkQDLVU/s1600/02.png)](http://3.bp.blogspot.com/-g8DBrvIgZWI/UcvtZzhR10I/AAAAAAAAAxI/zFqpHkQDLVU/s1600/02.png)</div></div>

* * *
<div>使用JObject可以簡化一點 </div><div><pre class="brush:csharp">// 淮備Json資料
JObject obj1 = new JObject()
{
    new JProperty("id", 1),
    new JProperty("name", "xian"),
    new JProperty("today", DateTime.Today),
    new JProperty("arraydata", 
    new JArray()
    {
        new JValue(1),
        new JValue(2),
        new JValue(3),
    })
};

string jsonString = obj1.ToString();
Console.WriteLine(jsonString);

// 解析Json格式
JObject obj2 = JObject.Parse(jsonString);
Console.WriteLine(
    "id:{0}, name:{1}, today:{2}, arraydata:{3}",
    obj2["id"],
    obj2["name"],
    obj2["today"],
    obj2["arraydata"]);
Console.ReadLine();
</pre></div><div>執行結果
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-l28UuWRqnjg/Ucvw4fibXHI/AAAAAAAAAxY/4PF_rybr6Gk/s1600/022.png)](http://2.bp.blogspot.com/-l28UuWRqnjg/Ucvw4fibXHI/AAAAAAAAAxY/4PF_rybr6Gk/s1600/022.png)</div></div>

* * *
<div>最常使用還是JsonConvert這一個方式，用法也很直覺 </div>
<div><pre class="brush:csharp">// 淮備資料
Person p1 = new Person()
{
    id = 1,
    name = "xian",
    today = DateTime.Today
};

// 序列化物件
string jsonString = JsonConvert.SerializeObject(p1);
Console.WriteLine("jsonstring:{0}", jsonString);

// 反序列化物件
Person p2 = JsonConvert.DeserializeObject&lt;Person&gt;(jsonString);
Console.WriteLine("id:{0}, name:{1}, today:{2}", p2.id, p2.name, p2.today);

Console.ReadLine();
</pre></div><div>執行結果
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-p0ZFI8Yk4qA/UcvtAucxvPI/AAAAAAAAAxA/BnB2RiseCNw/s1600/03.png)](http://4.bp.blogspot.com/-p0ZFI8Yk4qA/UcvtAucxvPI/AAAAAAAAAxA/BnB2RiseCNw/s1600/03.png)</div></div>