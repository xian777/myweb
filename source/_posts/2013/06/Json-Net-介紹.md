---
title: Json.Net 介紹
tags:
  - 'C#'
  - JSON
date: 2013-06-27 15:00:00
---

Json.Net 是一個第三方套件，其強大的功能和.Net內建的比較表，可以去[官網](http://james.newtonking.com/)看一下
個人比較有感覺的差別是

*   支援.Net 2.0
*   支援LINQ&nbsp;&nbsp;
*   支援暱名類別
*   支援dynamic物件
*   日期格式為ISO8601該專案為Open Source，可以到codeplex[下載原始碼 ](http://json.codeplex.com/)
安裝的方式也很簡單，打開NuGet輸入Json.Net就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-BDn6mLRndto/UcvaxUgwvEI/AAAAAAAAAww/fu0JjG4R5HE/s1600/01.png)](http://1.bp.blogspot.com/-BDn6mLRndto/UcvaxUgwvEI/AAAAAAAAAww/fu0JjG4R5HE/s1600/01.png)</div>Json.Net也有完整的[線上文件](http://james.newtonking.com/projects/json/help/)可以參考

以下是Json.Net常用的物件

<table border="1" cellpadding="3" cellspacing="1">                <tbody><tr>                        <td>[JsonConvert](http://james.newtonking.com/projects/json/help/index.html?topic=html/JsonNetVsDotNetSerializers.htm)</td>                        <td>最容易使用的一個靜態工具類別</td>                    </tr><tr>                        <td>[JsonTextReader](http://james.newtonking.com/projects/json/help/index.html?topic=html/JsonNetVsDotNetSerializers.htm)</td>                        <td>讀取Json格式</td>                    </tr><tr>                        <td>[JsonTextWriter](http://james.newtonking.com/projects/json/help/index.html?topic=html/JsonNetVsDotNetSerializers.htm)</td>                        <td>輸出Json格式</td>                    </tr><tr>                        <td>[JObject](http://james.newtonking.com/projects/json/help/index.html?topic=html/JsonNetVsDotNetSerializers.htm#)</td>                        <td>對應Json物件，就是大括號包起來的部份</td>                    </tr><tr>                        <td>[JArray](http://james.newtonking.com/projects/json/help/index.html?topic=html/JsonNetVsDotNetSerializers.htm#)</td>                        <td>對應Json陣列，就是中括號包起來的部份</td>                    </tr><tr>                        <td>[JValue](http://james.newtonking.com/projects/json/help/index.html?topic=html/JsonNetVsDotNetSerializers.htm#)</td>                        <td>對應Json值的部份</td>                    </tr></tbody>            </table>