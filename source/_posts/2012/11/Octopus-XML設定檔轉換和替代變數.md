---
title: Octopus XML設定檔轉換和替代變數
tags:
  - Octopus
  - XDT Transform
date: 2012-11-06 10:48:00
---

<div class="separator" style="clear: both; text-align: left;">專案佈署的過程中，不同環境的設定檔會有所不同，web.config使用的還是XDT Transform，只要檔名和環境別對的起來，就會自動轉換，例如UAT環境，佈署的時後，只要有web.uat.config這個檔案，就會自動轉換原來的web.config </div>
<div class="separator" style="clear: both; text-align: left;">除此之外，Octopus還有一些預先定義好的變數，可以在Variables裡面設定</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-y3E2E-vvY3k/UJh56tJ6rVI/AAAAAAAAATo/cx2IDuw-4NA/s1600/01.+Variables.png)](http://3.bp.blogspot.com/-y3E2E-vvY3k/UJh56tJ6rVI/AAAAAAAAATo/cx2IDuw-4NA/s1600/01.+Variables.png)</div>
<div class="separator" style="clear: both; text-align: left;">OctopusOriginalPackageDirectoryPath</div>這個變數用來指定套件佈署時的原來位置，例如 C:\Apps\Prod\MyApp\1.0.0

<div class="separator" style="clear: both; text-align: left;">OctopusPackageDirectoryPath</div>這個變數用來自訂套件要安裝的位置，例如D:\WebSite\MyApp

<div class="separator" style="clear: both; text-align: left;">OctopusWebSiteName</div>這個變數用來自訂站台的名稱，如不指定，則是以套件的名稱來對應IIS的設定

<div class="separator" style="clear: both; text-align: left;">更多詳細的設定，可以參考官網的文件</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">參考資料 </div>
<div class="separator" style="clear: both; text-align: left;">[Variables](http://octopusdeploy.com/documentation/features/variables)</div>
<div class="separator" style="clear: both; text-align: left;">[XML Configuration Files](http://octopusdeploy.com/documentation/features/xml-config)</div>
上一篇:[Octopus部署專案](http://blog.developer.idv.tw/2012/11/octopus_3840.html)
下一篇:[NuGet 套件超過30MB的問題](http://blog.developer.idv.tw/2012/11/nuget-30mb.html)