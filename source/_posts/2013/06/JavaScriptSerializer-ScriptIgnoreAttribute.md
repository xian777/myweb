---
title: JavaScriptSerializer ScriptIgnoreAttribute
tags:
  - 'C#'
  - JSON
date: 2013-06-19 17:47:00
---

<div>ScriptIgnore這個Attribute是用來取消屬性或欄位的序列化</div>
<div><pre class="brush:csharp">using System;
using System.Web.Script.Serialization;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            string jsonString = string.Empty;
            Data data = new Data()
            {
                Id = 1,
                Name = "data"
            };

            JavaScriptSerializer jss = new JavaScriptSerializer();
            jsonString = jss.Serialize(data);
            Console.WriteLine(jsonString);
            Console.ReadLine();
        }

        private class Data
        {
            public int Id { get; set; }
            public string Name { get; set; }
        }
    }
}
</pre></div>
<div>執行結果如下</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-PHlgEgUvvCM/UcF933vdXNI/AAAAAAAAAvI/ry4MXPXtNNc/s1600/02r1.png)](http://2.bp.blogspot.com/-PHlgEgUvvCM/UcF933vdXNI/AAAAAAAAAvI/ry4MXPXtNNc/s1600/02r1.png)</div>
加上ScriptIgnore這個Attribute之後
<div><pre class="brush:csharp">using System;
using System.Web.Script.Serialization;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            string jsonString = string.Empty;
            Data data = new Data()
            {
                Id = 1,
                Name = "data"
            };

            JavaScriptSerializer jss = new JavaScriptSerializer();
            jsonString = jss.Serialize(data);
            Console.WriteLine(jsonString);
            Console.ReadLine();
        }

        private class Data
        {
            public int Id { get; set; }

            [ScriptIgnore]
            public string Name { get; set; }
        }
    }
}
</pre></div><div>執行結果如下</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-NuSXZrS5PHg/UcF97o95C-I/AAAAAAAAAvQ/7WrPyRw6dqU/s1600/02r2.png)](http://2.bp.blogspot.com/-NuSXZrS5PHg/UcF97o95C-I/AAAAAAAAAvQ/7WrPyRw6dqU/s1600/02r2.png)</div>