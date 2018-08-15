---
title: NLog Layouts
tags:
  - NLog
date: 2012-12-30 16:47:00
---

## NLog Layouts
<div>Layout是用來決定記錄的訊息輸出的格式，通常設定在target的屬性中</div><div>這個功能可以讓我們動態增減日誌的內容，而不用回頭修改程式碼和重新編譯</div><div>使用方法是$字號和左右大括號，包住Layout Renderers</div><div>參數的使用方法則是冒號分隔，屬性=值的方式</div><div>預設的輸出格式如下</div><div>
</div><div><pre class="brush:xml">${longdate}|${level:uppercase=true}|${logger}|${message}</pre></div><div><div>
</div>

* * *
<div>

## Layout Renderers
</div></div><div>

*   ${basedir} - 應用程式所在的資料庫
*   ${callsite} - 日誌來源的類別名稱、方法名稱和來源資訊
*   ${data} - 目前日期和時間
*   ${exception} - 例外的訊息
*   ${level} - 日誌的級別
*   ${logger} - 日誌的來源
*   ${logdate} - 長日期格式，yyyy-MM-dd HH:mm:ss.mmm
*   ${machinename} - 電腦名稱
*   ${message} - 日誌的內容
*   ${newline} - 換行符號
*   ${shortdate} - 短日期格式 &nbsp;yyyy-MM-dd
*   ${stacktrace} - 呼叫堆疊資訊
*   ${time} - 時間格式，HH:mm:ss.mmm.
*   ${windows-identity} - 登入帳號</div><div>每一個Layout Renderers還包含各自的屬性，詳細的內容可以參考[官網Layout Renderers文件](https://github.com/NLog/NLog/wiki/Layout-renderers)

* * *

## Pre-Defined Layouts
NLog還包含了幾個預設定義好的格式，詳細的文件請參考[官網的Layout文件](https://github.com/NLog/NLog/wiki/Layouts)

*   CsvLayout - CSV格式
*   LayoutWithHeaderAndFooter - 加上Header和Footer的格式
*   Log4JXmlEventLayout - Log4j相容的格式
*   SimpleLayout - 簡單的文字內容格式

<div>上一篇 : [NLog Rules](http://blog.developer.idv.tw/2012/12/nlog-rules.html)</div>

</div>