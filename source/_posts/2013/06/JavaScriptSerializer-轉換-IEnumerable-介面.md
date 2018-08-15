---
title: JavaScriptSerializer 轉換 IEnumerable 介面
tags:
  - 'C#'
  - JSON
date: 2013-06-18 18:39:00
---

<div>一樣開新Console專案做示範，並加入System.Web.Extensions.dll參考
完整的程式碼如下</div><div><pre class="brush:csharp">using System;
using System.Collections.Generic;
using System.Web.Script.Serialization;

namespace JavaScriptSerializerDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 淮備要序列化的資料
            List&lt;JsonObject&gt; data = new List&lt;JsonObject&gt;()
            {
                new JsonObject()
                {
                    ID = 1,
                    Name = "JsonObject1",
                    State = EnumState.a,
                    Date = DateTime.Today.AddDays(-1),
                    GUID = Guid.NewGuid()
                },
                new JsonObject()
                {
                    ID = 2,
                    Name = "JsonObject2",
                    State = EnumState.b,
                    Date = DateTime.Today,
                    GUID = Guid.NewGuid()
                },
                new JsonObject()
                {
                    ID = 3,
                    Name = "JsonObject3",
                    State = EnumState.c,
                    Date = DateTime.Today.AddDays(1),
                    GUID = Guid.NewGuid()
                },
            };

            // 序列化
            JavaScriptSerializer jss = new JavaScriptSerializer();
            string jsonString = jss.Serialize(data);
            Console.WriteLine("序列化的JSON字串:{0}\r\n", jsonString);

            // 反序列化
            List&lt;JsonObject&gt; obj = jss.Deserialize&lt;List&lt;JsonObject&gt;&gt;(jsonString);
            foreach (var item in obj)
            {
                Console.WriteLine(
                    "反序列化後的物件, ID:{0}, Name:{1}, State:{2}, Date:{3}, GUID:{4}",
                    item.ID,
                    item.Name,
                    item.State,
                    item.Date,
                    item.GUID);
            }

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
</pre></div><div>
序列化後的結果</div><div><pre class="brush:javascript">[
  {
    "ID": 1,
    "Name": "JsonObject1",
    "State": 0,
    "Date": "\/Date(13713984 00000)\/",
    "GUID": "97eff121-b03d-4c76-9d18-1a82660f3f40"
  },
  {
    "ID": 2,
    "Name": "JsonObject2",
    "State": 1,
    "Date": "\/Date(1371484800000)\/",
    "GUID": "2fa2f230-d721-4c21-9630 -a90657bb4aac"
  },
  {
    "ID": 3,
    "Name": "JsonObject3",
    "State": 2,
    "Date": "\/Date(1371571200 000)\/",
    "GUID": "e8a8462f-7c59-4f34-a895-484f2be13bd7"
  }
]</pre></div><div>執行的結果 </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-LNUNck-sUA4/UcA3p_YRqvI/AAAAAAAAAuQ/3cU_FdYALX8/s1600/03.Result02.png)](http://1.bp.blogspot.com/-LNUNck-sUA4/UcA3p_YRqvI/AAAAAAAAAuQ/3cU_FdYALX8/s1600/03.Result02.png)</div>