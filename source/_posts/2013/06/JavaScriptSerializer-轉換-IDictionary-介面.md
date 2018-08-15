---
title: JavaScriptSerializer 轉換 IDictionary 介面
tags:
  - 'C#'
  - JSON
date: 2013-06-18 18:40:00
---

<div>一樣開個新的Console專案，和加入System.Web.Extensions.dll參考
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
            Dictionary&lt;string, object&gt; data = new Dictionary&lt;string, object&gt;()
            {
                {
                    "ID", 1
                },
                {
                    "Name", "Dictionary Demo"
                },
                {
                    "State", EnumState.c
                },
                {
                    "Date", DateTime.Today
                },
                {
                    "Guid", Guid.NewGuid()
                }
            };

            // 序列化
            JavaScriptSerializer jss = new JavaScriptSerializer();
            string jsonString = jss.Serialize(data);
            Console.WriteLine("序列化的JSON字串:{0}\r\n", jsonString);

            // 反序列化
            JsonObject obj = jss.Deserialize&lt;JsonObject&gt;(jsonString);
            Console.WriteLine(
                "反序列化後的物件, ID:{0}, Name:{1}, State:{2}, Date:{3}, GUID:{4}\r\n",
                obj.ID,
                obj.Name,
                obj.State,
                obj.Date,
                obj.GUID);

            Dictionary&lt;string, object&gt; dict = jss.Deserialize&lt;Dictionary&lt;string, object&gt;&gt;(jsonString);
            Console.WriteLine("反序列化回Dictionary");
            foreach (var key in dict.Keys)
            {
                Console.WriteLine("Key:{0}, Value:{1}", key, dict[key]);
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

</pre></div>
<div>序列化後的JSON </div><div><pre class="brush:javascript">{
  "ID": 1,
  "Name": "Dictionary Demo",
  "State": 2,
  "Date": "\/Date(13714 84800000)\/",
  "Guid": "7c52f0a4-a742-4898-a55c-583ab851b183"
}
</pre></div><div>
輸出的結果
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-B-mVNtMsiRk/UcAx1cKBfDI/AAAAAAAAAtw/2Cz6mRMH_hI/s1600/03.+Result03.png)](http://1.bp.blogspot.com/-B-mVNtMsiRk/UcAx1cKBfDI/AAAAAAAAAtw/2Cz6mRMH_hI/s1600/03.+Result03.png)</div></div>