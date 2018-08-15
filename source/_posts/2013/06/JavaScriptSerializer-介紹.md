---
title: JavaScriptSerializer 介紹
tags:
  - 'C#'
  - JSON
date: 2013-06-18 18:39:00
---

JavaScriptSerializer是.NET 3.5中新增的類別
該類別在System.Web.Script.Serialization命名空間下面
需引用System.Web.Extensions.dll

方法
<table border="1" cellpadding="3" cellspacing="1">                <tbody><tr>                        <td>[Serialize](http://msdn.microsoft.com/zh-tw/library/system.web.script.serialization.javascriptserializer.serialize%28v=vs.90%29.aspx)</td>                        <td>將物件序列化成JSON字串</td>                    </tr><tr>                        <td>[Deserialize&lt;T&gt;](http://msdn.microsoft.com/zh-tw/library/bb355316%28v=vs.90%29.aspx)</td>                        <td>將JSON字串反序列化成指定的物件</td>                    </tr></tbody>            </table>

屬性
<table border="1" cellpadding="3" cellspacing="1">                <tbody><tr>                        <td>[MaxJsonLength](http://msdn.microsoft.com/zh-tw/library/system.web.script.serialization.javascriptserializer.maxjsonlength%28v=vs.90%29.aspx)</td>                        <td>取得或設定可接受的字串最大長度，預設為4MB</td>                    </tr><tr>                        <td>[RecursionLimit](http://msdn.microsoft.com/zh-tw/library/system.web.script.serialization.javascriptserializer.recursionlimit%28v=vs.90%29.aspx)</td>                        <td>取得或設定要處理物件層級數目的限制</td>                    </tr></tbody>            </table>
參考資料

[System.Web.Script.Serialization 命名空間](http://msdn.microsoft.com/zh-tw/library/bb359469%28v=vs.90%29.aspx)