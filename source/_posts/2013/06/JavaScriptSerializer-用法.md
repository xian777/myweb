---
title: JavaScriptSerializer 用法
tags:
  - 'C#'
  - JSON
date: 2013-06-18 18:39:00
---

<div>首先開一個Console專案</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-VwDQgSVGz-U/UcAj3KvmOLI/AAAAAAAAAtI/Kf254EFNRiY/s1600/01.NewProject.png)](http://1.bp.blogspot.com/-VwDQgSVGz-U/UcAj3KvmOLI/AAAAAAAAAtI/Kf254EFNRiY/s1600/01.NewProject.png)</div><div>加入System.Web.Extensions.dll的引用</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-nxGL-_thS3A/UcAkAWtjyxI/AAAAAAAAAtQ/BRmfRy3LwFM/s1600/02.AddReference.png)](http://2.bp.blogspot.com/-nxGL-_thS3A/UcAkAWtjyxI/AAAAAAAAAtQ/BRmfRy3LwFM/s1600/02.AddReference.png)</div><div>完整的程式碼如下</div><div><pre class="brush:csharp">using System;
using System.Web.Script.Serialization;

namespace JavaScriptSerializerDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 淮備要序列化的資料
            JsonObject data = new JsonObject()
            {
                ID = 1,
                Name = "JsonObject",
                State = EnumState.c,
                Date = DateTime.Today,
                GUID = Guid.NewGuid()
            };

            // 序列化
            JavaScriptSerializer jss = new JavaScriptSerializer();
            string jsonString = jss.Serialize(data);
            Console.WriteLine("序列化的JSON字串:{0}\r\n", jsonString);

            // 反序列化
            JsonObject obj = jss.Deserialize&lt;JsonObject&gt;(jsonString);
            Console.WriteLine(
                "反序列化後的物件, ID:{0}, Name:{1}, State:{2}, Date:{3}, GUID:{4}",
                obj.ID,
                obj.Name,
                obj.State,
                obj.Date,
                obj.GUID);

            Console.ReadLine();
        }

        /// &lt;summary&gt;
        /// 要序列化的資料類別
        /// &lt;/summary&gt;
        private class JsonObject
        {
            public int ID { get; set; }
            public string Name { get; set; }
            public EnumState State { get; set; }
            public DateTime Date { get; set; }
            public Guid GUID { get; set; }
        }

        /// &lt;summary&gt;
        /// 狀態列舉
        /// &lt;/summary&gt;
        public enum EnumState
        {
            a = 0,
            b = 1,
            c = 2
        }
    }
}
</pre></div><div>序列化的JSON字串 
<pre class="brush:csharp">{
  "ID": 1,
  "Name": "JsonObject",
  "State": 2,
  "Date": "\/Date(1371484800 000)\/",
  "GUID": "80d39299-a127-459f-b6ef-55626c490f80"
}</pre></div>
<div>執行的結果
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-no6cdwZCVzo/UcA2jzMJbPI/AAAAAAAAAuA/1mlIoyjrQdg/s1600/03.Result01.png)](http://2.bp.blogspot.com/-no6cdwZCVzo/UcA2jzMJbPI/AAAAAAAAAuA/1mlIoyjrQdg/s1600/03.Result01.png)</div>
<div class="separator" style="clear: both; text-align: center;"></div></div>