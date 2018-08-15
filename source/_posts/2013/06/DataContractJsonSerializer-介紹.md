---
title: DataContractJsonSerializer 介紹
tags:
  - 'C#'
  - JSON
date: 2013-06-20 14:35:00
---

<div>JavaScriptSerializer是.NET 3.5中新增的類別
該類別在System.Runtime.Serialization.Json命名空間下面
需引用System.Runtime.Serialization.dll</div><div>建構式 </div><div><table border="1" cellpadding="3" cellspacing="1">                <tbody><tr>                        <td>[DataContractJsonSerializer(Type)](http://msdn.microsoft.com/zh-tw/library/bb908625.aspx)</td>                        <td>傳入要轉換的資料型別</td>                    </tr><tr>                        <td>[DataContractJsonSerializer(Type, DataContractJsonSerializerSettings)](http://msdn.microsoft.com/zh-tw/library/hh194418.aspx)</td>                        <td>傳入要轉換的資料型別，和設定值</td>                    </tr></tbody>            </table></div>
<div>方法 </div><div><table border="1" cellpadding="3" cellspacing="1">                <tbody><tr>                        <td>[WriteObject](http://msdn.microsoft.com/zh-tw/library/system.runtime.serialization.json.datacontractjsonserializer.writeobject.aspx)
</td>                        <td>將物件序列化成JSON字串</td>                    </tr><tr>                        <td>[ReadObject](http://msdn.microsoft.com/zh-tw/library/system.runtime.serialization.json.datacontractjsonserializer.readobject.aspx)
</td>                        <td>將JSON字串反序列化成指定的物件</td>                    </tr></tbody>            </table></div>
<div>參考資料

[System.Runtime.Serialization.Json 命名空間](http://msdn.microsoft.com/zh-tw/library/system.runtime.serialization.json.aspx)</div>