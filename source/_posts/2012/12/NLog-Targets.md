---
title: NLog Targets
tags:
  - NLog
date: 2012-12-30 00:29:00
---

## NLog Targets
target用來定義Log的輸出目標，基本的兩個屬性為

*   name - 目標的名稱，用來給rule路由指定的名稱
*   type - 目標的類型，NLog支援的類型很多，完整資料請參考[官網Supported Targets文件](https://github.com/nlog/nlog/wiki/Targets)每一個target元素代表一個輸出目標，只要name屬性值不衝突即可
<pre class="brush:xml">&lt;targets&gt;
    &lt;target name="f1" xsi:type="File" fileName="file1.txt"/&gt;
    &lt;target name="f2" xsi:type="File" fileName="file2.txt"/&gt;
    &lt;target name="n1" xsi:type="Network" address="tcp://localhost:4001"/&gt;
    &lt;target name="ds" xsi:type="OutputDebugString"/&gt;
&lt;/targets&gt;
</pre>
依照type的不同，會有相對應的屬性，例如
File需要指定FileName檔名
Database需指定資料庫相關的參數和語法
Mail需指定郵件主機等資訊
每種類型的設定方式，之後再來詳細介紹

* * *

## 自訂target
要自行擴充target可以參考官網文件的[How to write a target](https://github.com/nlog/nlog/wiki/How%20to%20write%20a%20Target)
只要繼承NLog的TargetWithLayout類別，覆寫Write(LogEventInfo logEvent)函式
再利用extensions元素或在程式碼中註冊就行了

* * *

## Wrapper Targets
<div>NLog提供幾個封裝和複合目標，用來增加target的功能</div><div>

*   asynchronous processing (非同步功能，被封裝的target會由另一個執行緒來運行)
*   retry-on-error(自動重試功能)
*   buffering(緩衝處理，不會馬上寫出Log，而會依設定值累積一定數量才輸出Log)
*   filtering(過濾條件，會依設定值決定是否輸出Log)<div>更多詳細功能請參考[官網的Wrapper Targets文件](https://github.com/nlog/nlog/wiki/Targets)</div></div><div>
</div><div>Wrapper可以連續嵌套，以下的範例可以增加非同步和自動重試的功能</div><pre class="brush:xml">&lt;targets&gt;
    &lt;!-- 增加非同步功能--&gt;
    &lt;target name="n" xsi:type="AsyncWrapper"&gt;
        &lt;!-- 增加自動重試功能 --&gt;
        &lt;target xsi:type="RetryingWrapper"&gt;
            &lt;target xsi:type="File" fileName="${file}.txt" /&gt;
        &lt;/target&gt;
    &lt;/target&gt;
&lt;/targets&gt;
</pre><div>
由於非同步處理是很常用來增加效能的功能，所以提供了一個更簡單的設定方式

</div><pre class="brush:xml">&lt;nlog&gt;
    &lt;targets async="true"&gt;
        &lt;!-- 放在這個section之間的target都會有非同步功能 --&gt;
    &lt;/targets&gt;
&lt;/nlog&gt;
</pre>

* * *

## Default wrappers
<div>如果有多組target元素需要大腸包小腸的時後，多層的嵌套會比較複雜
所以提供了預設封裝的功能
使用default-wrapper元素設定，同一組的target就會有同樣的封裝功能</div><div><pre class="brush:xml">&lt;nlog&gt;
    &lt;!-- 第一組Wrapper --&gt;
    &lt;targets&gt;
        &lt;default-wrapper xsi:type="BufferingWrapper" bufferSize="100"/&gt;  
        &lt;target name="f1" xsi:type="File" fileName="f1.txt"/&gt;  
        &lt;target name="f2" xsi:type="File" fileName="f2.txt"/&gt;  
    &lt;/targets&gt;
    &lt;!-- 第二組Wrapper --&gt;
    &lt;targets&gt;  
        &lt;default-wrapper xsi:type="AsyncWrapper"&gt;  
            &lt;wrapper xsi:type="RetryingWrapper"/&gt;  
        &lt;/default-wrapper&gt;  
        &lt;target name="n1" xsi:type="Network" address="tcp://localhost:4001"/&gt;  
        &lt;target name="n2" xsi:type="Network" address="tcp://localhost:4002"/&gt;  
        &lt;target name="n3" xsi:type="Network" address="tcp://localhost:4003"/&gt;  
    &lt;/targets&gt; 
&lt;/nlog&gt;
</pre></div>

* * *

## Default target parameters
<div>類似的功能在參數設定上也有
同一組的target需要設定同樣的參數設定的話，也可以利用這個功能設定一次就好</div><div><pre class="brush:xml">&lt;nlog&gt;
    &lt;targets&gt;
        &lt;!-- 多組target都有同樣的屬性keepFileOpen --&gt;
        &lt;target name="f1" xsi:type="File" fileName="f1.txt" keepFileOpen="false"/&gt;
        &lt;target name="f2" xsi:type="File" fileName="f2.txt" keepFileOpen="false"/&gt;
        &lt;target name="f3" xsi:type="File" fileName="f3.txt" keepFileOpen="false"/&gt;
    &lt;/targets&gt;
&lt;/nlog&gt;
&lt;!-- 替代的設定方式如下 --&gt;
&lt;nlog&gt;
    &lt;targets&gt;
        &lt;!-- 利用default-target-parameters來設定一次就好 --&gt;
        &lt;default-target-parameters xsi:type="File" keepFileOpen="false"/&gt;
        &lt;target name="f1" xsi:type="File" fileName="f1.txt"/&gt;
        &lt;target name="f2" xsi:type="File" fileName="f2.txt"/&gt;
        &lt;target name="f3" xsi:type="File" fileName="f3.txt"/&gt;
    &lt;/targets&gt;
&lt;/nlog&gt;
</pre></div><div>

上一篇 : [NLog Config](http://blog.developer.idv.tw/2012/12/nlog-config.html)
下一篇 : [NLog Rules](http://blog.developer.idv.tw/2012/12/nlog-rules.html)</div>