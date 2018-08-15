---
title: TeamCity 建置後打包和發佈套件
tags:
  - NuGet
  - TeamCity
date: 2012-11-13 23:04:00
---

<div class="separator" style="clear: both; text-align: left;">先溫習一下NuGet打包和發佈的方式 </div>
<div class="separator" style="clear: both; text-align: left;">[建立NuGet套件 ](http://blog.developer.idv.tw/2012/10/nuget_21.html)</div>
<div class="separator" style="clear: both; text-align: left;">接下來按照打包的方式來作業，新增一個Build Step為NuGetPack</div>選擇NuGet執行檔的版本，再選擇專案檔的路徑
Version是建置時後的版本，最後是輸出的資料夾

<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-Pyj4DdHcPGQ/UKJg1gT5ksI/AAAAAAAAAdI/iXtQOOhP51c/s1600/01.NugetPack.png)](http://1.bp.blogspot.com/-Pyj4DdHcPGQ/UKJg1gT5ksI/AAAAAAAAAdI/iXtQOOhP51c/s1600/01.NugetPack.png)</div><div class="separator" style="clear: both; text-align: left;">因為增加了套件輸出的路徑，所以回到General Settings</div>在Artifact paths也增加套件輸出的路徑
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-QxFU1xxqx04/UKJhPtSoFqI/AAAAAAAAAdQ/9s6gOq3iZfM/s1600/02.ArtifactPaths.png)](http://1.bp.blogspot.com/-QxFU1xxqx04/UKJhPtSoFqI/AAAAAAAAAdQ/9s6gOq3iZfM/s1600/02.ArtifactPaths.png)</div>
<div class="separator" style="clear: both; text-align: left;">設定完成後再次建置，建置成功就會在Artifacts得到套件</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-u8ub2aXW8pc/UKJhQFcK60I/AAAAAAAAAdY/GulIFxNyNPE/s1600/03.BuildSuccess.png)](http://3.bp.blogspot.com/-u8ub2aXW8pc/UKJhQFcK60I/AAAAAAAAAdY/GulIFxNyNPE/s1600/03.BuildSuccess.png)</div>
<div class="separator" style="clear: both; text-align: left;">接下來再新增一個Build Step，選擇NuGetPublish</div>選擇NuGet執行檔的版本，輸入NuGet Server的網址和api key
再選擇要上傳的套件，下次建置的時後，就會一起發佈出去了 
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Axp5HdttthA/UKJhQ3jst5I/AAAAAAAAAdg/hrhTgMC4uzU/s1600/04.Publish.png)](http://2.bp.blogspot.com/-Axp5HdttthA/UKJhQ3jst5I/AAAAAAAAAdg/hrhTgMC4uzU/s1600/04.Publish.png)</div>
<div class="separator" style="clear: both; text-align: left;">上一篇:[TeamCity 建置前先還原NuGet套件](http://blog.developer.idv.tw/2012/11/teamcity-nuget.html)</div><div class="separator" style="clear: both; text-align: left;">下一篇:[TeamCity 改用網域帳號LDAP登入](http://blog.developer.idv.tw/2012/11/teamcity-ldap.html)</div>