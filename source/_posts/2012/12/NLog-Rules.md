---
title: NLog Rules
tags:
  - NLog
date: 2012-12-30 01:40:00
---

## NLog Rules
<div>NLog使用一個簡單的路由表檢查</div><div>當檢查到符合的日誌名稱和級別時，會輸出到指定的一個或多個Target去</div><div>如果指定了final屬性，之後的規則就不再檢查</div><div>Rules可以使用的屬性如下</div><div>
</div><div>

1.  name - 日誌來源的名稱(允許使用通配符號*)
2.  minlevel - 設定符合該規則的最低級別
3.  maxlevel - 設定符合該規則的最高級別
4.  level - 設定符合該規則的特定級別
5.  levels - 設定符合該規則的級別列表，用逗號分隔
6.  writeTo - 設定符合該規則的日誌要寫入的target列表，用逗號分隔
7.  final - 設定符合該規則的條件為最後一個規則，後面的規則不再檢查<div>以下為一些例子</div></div><div><pre class="brush:xml">&lt;!-- 命名空間Name.Space下的Class1這個類別的日誌，符合Debug以上的級別，就輸出到f1這個Target --&gt;
&lt;logger name="Name.Space.Class1" minlevel="Debug" writeTo="f1" /&gt;

&lt;!-- 命名空間Name.Space下的Class1這個類別的日誌，符合Debug和Error這兩個級別，就輸出到f1這個Target --&gt;
&lt;logger name="Name.Space.Class1" levels="Debug,Error" writeTo="f1" /&gt;

&lt;!-- 命名空間Name.Space下的所有類別的日誌，就輸出到f3和f4這兩個Target --&gt;
&lt;logger name="Name.Space.*" writeTo="f3,f4" /&gt;

&lt;!-- 
    命名空間Name.Space下的所有類別的日誌，級別在Debug和Error之間
    也就是說級別為Debug, Info, Warn, Error，不輸出日誌，因為這條規則沒有指定writeTo
    同時不再檢查之後的規則，因為這裡設定final=true
--&gt;
&lt;logger name="Name.Space.*" minlevel="Debug" maxlevel="Error" final="true" /&gt;
</pre></div>

* * *

## NLog Level
NLog的日誌級別分為六個等級，方便我們對於不同情境制訂出合適的級別輸出

1.  Trace - 大量而詳細的訊息，一般只用在開發環境
2.  Debug - 用來除錯用的詳細訊息，比Trace用的少一點，一般也只用在開發環境
3.  Info - 用來提示用的訊息，例如使用者登出入，交易參數資料
4.  Warn - 用來警告用的訊息，例如執行時間超出預期，連線數接近上限
5.  Error - 一般錯誤的訊息，一般就是try catch到的Exception
6.  Fatal - 致命錯誤的訊息，通常會造成應用程式無法執行<div>最簡單的設定檔配置，只要設定Rule和要寫入的Target就行了</div><div>
上一篇: [NLog Targets](http://blog.developer.idv.tw/2012/12/nlog-targets.html)
下一篇: [NLog Layouts&nbsp;](http://blog.developer.idv.tw/2012/12/nlog-layouts.html)</div>