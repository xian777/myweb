---
title: JSON筆記
tags:
  - JSON
date: 2013-06-18 18:39:00
---

JSON 筆記

JSON的全名為JavaScript Object Notation，是JavaScript的物件表示法
因為輕量化，易於人閱讀和編寫，也易於機器解析和生成的關系，所以很容易在各種網絡平台和程序之間做為一種資料交換格式

JSON的內容主要有二種型態，一種是物件，一種是陣列
物件由大括號包起來，屬性和值用冒號來分隔，每個屬性之間用逗點分隔
陣列用中括號包起來，每個資料之間用逗點分隔
<div><pre class="brush:javascript">{
  "ID": 1,
  "Name": "JSON Demo",
  "State": 2,
  "Date": "\/Date(13714 84800000)\/",
  "Guid": "7c52f0a4-a742-4898-a55c-583ab851b183",
  "DataList": [
    1,
    2,
    3,
    4,
    5
  ]
}
</pre></div>
JSON的資料型態有文字、數字、布林、NULL
文字:用雙引號包起來的內容
數字:包含整數和浮點數
布林: true / false
更多完整的介紹，可以參考官網或W3CSchool

[JSON官網介紹](http://www.json.org/json-zh.html)

[W3CSchool Learn JSON](http://www.w3schools.com/json/default.asp)

* * *
在.NET中內建兩種解析方式，但需要Framework 3.5以上

System.Web.Extensions下面的JavaScriptSerializer
[JavaScriptSerializer 介紹](http://blog.developer.idv.tw/2013/06/javascriptserializer.html)
[JavaScriptSerializer 用法](http://blog.developer.idv.tw/2013/06/javascriptserializer_18.html)
[JavaScriptSerializer 轉換 IEnumerable 介面](http://blog.developer.idv.tw/2013/06/javascriptserializer-ienumerable.html)
[JavaScriptSerializer 轉換 IDictionary 介面](http://blog.developer.idv.tw/2013/06/javascriptserializer-idictionary.html)
[JavaScriptSerializer 日期處理](http://blog.developer.idv.tw/2013/06/javascriptserializer_19.html)
[JavaScriptSerializer ScriptIgnoreAttribute](http://blog.developer.idv.tw/2013/06/javascriptserializer_7623.html)

* * *

System.Runtime.Serialization下面的DataContractJsonSerializer
[DataContractJsonSerializer 介紹](http://blog.developer.idv.tw/2013/06/datacontractjsonserializer.html) 
[DataContractJsonSerializer 用法](http://blog.developer.idv.tw/2013/06/datacontractjsonserializer_20.html)
[DataContractJsonSerializer 轉換 IEnumerable 介面](http://blog.developer.idv.tw/2013/06/datacontractjsonserializer-ienumerable.html)
[DataContractJsonSerializer 轉換 IDictionary 介面](http://blog.developer.idv.tw/2013/06/datacontractjsonserializer-idictionary.html) 
[DataContractJsonSerializer 日期處理](http://blog.developer.idv.tw/2013/06/datacontractjsonserializer_6717.html)

* * *

另外還有一個好用的第三方套件JSON.Net
[Json.Net 介紹](http://blog.developer.idv.tw/2013/06/jsonnet_27.html)
[Json.Net 用法](http://blog.developer.idv.tw/2013/06/jsonnet.html)
[Json.Net 轉換 IEnumerable 介面](http://blog.developer.idv.tw/2013/06/jsonnet-ienumerable.html)
[Json.Net 轉換 IDictionary 介面](http://blog.developer.idv.tw/2013/06/jsonnet-idictionary.html)
[Json.Net 日期處理](http://blog.developer.idv.tw/2013/07/jsonnet.html)

* * *

另外介紹幾個好用的工具
[Online JSON Viewer](http://jsonviewer.stack.hu/)
一個用來方便格式化JSON字串的網站 

[JSON2CSharp](http://json2csharp.com/)
一個用來產生C#對應類別的網站

[JSON C# Class Generator](http://jsonclassgenerator.codeplex.com/)
一個用來產生C#對應類別的程式

[JSONLint - The JSON Validator](http://jsonlint.com/)