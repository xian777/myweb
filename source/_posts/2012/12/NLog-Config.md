---
title: NLog Config
tags:
  - NLog
date: 2012-12-29 16:27:00
---

## NLog設定檔位置
NLog的設定檔有幾個位置，參考[官網文件](https://github.com/nlog/nlog/wiki/Configuration-file)如下

1.  應用程式的標準設定檔(app.config或是web.config)
<span style="color: orange;">執行過程中如果需要修改NLog的配置，會造成應用程式重新啟動</span>
2.  應用程式所在目錄的app.exe.nlog
<span style="color: orange;">每個專案都要手動指定檔名比較麻煩點</span>
3.  應用程式所在目錄的NLog.config
<span style="color: red;">建議使用的設定檔方式</span>
4.  Nlog.dll所在目錄的NLog.dll.config
<span style="color: orange;">和第三種方式差不多，還是選擇比較常見的第三種方式吧</span>
5.  環境變數NLOG_GLOBAL_CONFIG_FILE指定的檔案
<span style="color: orange;">設在這種神秘的地方，應該會被扁吧</span><div>在ASP.NET或是Windows Form應用程式中有點差異，其他的專案類型有幾種方式不能用，所以建議使用最通用的第三種方式</div>

* * *

## NLog設定檔元素
<div>Nlog的設定檔有以下五種元素，前兩種是必要項目，後三種是可選項目</div><div>

1.  targets - 定義Log的輸出目標，輸出格式的Layout也在這裡設定
2.  rules - 定義Log的路由規則，Log的過濾條件也在這裡設定
3.  extensions - 定義擴充元件，包含NLog擴充模組和自定義的擴充模組
4.  include - 引用外部設定檔，簡化設定檔的複雜度和重覆利用
5.  variable - 定義設定檔中自行設定的變數，可以統一和簡化設定檔資料</div><div>

* * *

## NLog設定檔自動重讀
NLog的設定檔，在執行過程中預設是不會重讀的，每個修改都需要重新啟動應用程式才能生效
如果要自動重讀的話，需要設定一個屬性autoReload="true"才能生效

<pre class="brush:xml">&lt;nlog autoreload="true"&gt;
   ...
&lt;/nlog&gt;
</pre></div>

* * *

## NLog設定檔疑難排解
<div>有時後就算設好了設定檔，Log還是沒有寫出來，最常見的原因是權限問題造成的問題</div><div>例如ASP.NET的w3wp.exe沒有指定資料夾寫檔案的權限</div><div>這時後可以利用NLog內部的Log來查詢原因</div><div>

1.  throwExceptions -&nbsp;設定是否要引發錯誤
<span style="color: orange;">NLog會吃掉所有內部引發的錯誤，要找問題時可以設為true，找到之後應該設回false</span>
2.  internalLogFile - 設定內部錯誤要輸出的文件位置
<span style="color: orange;">直接給一個檔名就好，會輸出在執行檔所在目錄下面</span>
3.  internalLogLevel - 設定內部錯誤要輸出的層級
<span style="color: orange;">基本上要找的是Error訊息比較簡潔點，不設定的話會輸出所有詳細訊息</span>
4.  internalLogToConsole - 設定內部錯誤是否要輸出到Console視窗
<span style="color: orange;">如果不想寫檔，又有Console可以用的話，那就設定為true吧</span>
5.  internalLogToConsoleError - 設定內部錯誤是否要輸出到stderr串流
<span style="color: orange;">為了不要和應用程式正常訊息混在一起，可以把錯誤訊息重導向到stderr</span><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-3xE3_wOWE3M/UN6pAVTohrI/AAAAAAAAAos/s4mfqjO6UQc/s1600/01.+InternalError.png)](http://3.bp.blogspot.com/-3xE3_wOWE3M/UN6pAVTohrI/AAAAAAAAAos/s4mfqjO6UQc/s1600/01.+InternalError.png)</div><div>
</div></div><div class="separator" style="clear: both; text-align: left;">上一篇 : [NLog 初體驗](http://blog.developer.idv.tw/2012/12/nlog.html)</div>下一篇 : [NLog Targets](http://blog.developer.idv.tw/2012/12/nlog-targets.html)