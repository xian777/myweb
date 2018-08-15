---
title: 使用NuGet安裝、移除、更新套件
tags:
  - NuGet
date: 2012-10-12 11:15:00
---

<div style="clear: both; text-align: left;">NuGet主要的功能，是新增、移除、更新套件，接下來就介紹這幾個功能 </div>
<div style="clear: both; text-align: left;">

# 

* * *
GUI介面
可以很方便地新增和移除套件 </div>
<div style="clear: both; text-align: left;">在專案參考上面按右鍵</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-XS3ZrSz7Sz8/UHeGBweDbVI/AAAAAAAAAHA/OLOYGXSeVMo/s1600/01.GUI.png)](http://3.bp.blogspot.com/-XS3ZrSz7Sz8/UHeGBweDbVI/AAAAAAAAAHA/OLOYGXSeVMo/s1600/01.GUI.png)</div>
<div style="clear: both; text-align: left;">出現的GUI視窗，左邊可以選擇來源，中間選擇套件，右上角則是搜尋方塊
以JQuery為列，直接按安裝就好了</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-CY2Pd35x9bw/UHeIXhJTIoI/AAAAAAAAAHY/IvSXqNbp9AI/s1600/02.install.png)](http://4.bp.blogspot.com/-CY2Pd35x9bw/UHeIXhJTIoI/AAAAAAAAAHY/IvSXqNbp9AI/s1600/02.install.png)</div>
<div style="clear: both; text-align: left;">安裝成功</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-JfubxHCmqiM/UHeETIUq3RI/AAAAAAAAAG4/ZmOCOd0Isfg/s1600/03.InstallOK.png)](http://1.bp.blogspot.com/-JfubxHCmqiM/UHeETIUq3RI/AAAAAAAAAG4/ZmOCOd0Isfg/s1600/03.InstallOK.png)</div>
<div style="clear: both; text-align: left;">如果要解除安裝，選擇左邊的「已安裝的套件」，然後選擇解除安裝就好了</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-S4d5AIcFThY/UHeGCUqmjeI/AAAAAAAAAHI/Sb-5Z8cqIV0/s1600/04.UnInstall.png)](http://2.bp.blogspot.com/-S4d5AIcFThY/UHeGCUqmjeI/AAAAAAAAAHI/Sb-5Z8cqIV0/s1600/04.UnInstall.png)</div>
<div style="clear: both; text-align: left;">解除安裝成功</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-bxdHPUljs7w/UHeGEVtQXrI/AAAAAAAAAHM/_yoePcov-cc/s1600/05.UnInstallOK.png)](http://3.bp.blogspot.com/-bxdHPUljs7w/UHeGEVtQXrI/AAAAAAAAAHM/_yoePcov-cc/s1600/05.UnInstallOK.png)</div>
<div style="clear: both; text-align: left;">

* * *

# Console介面
功能比較完整，也可以使用Tab命令補全 </div>
<div style="clear: both; text-align: left;">選擇工具裡面的程式庫套件管理員，再選擇Package Manager Console</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-UwUWUKz-yBQ/UHeJVA0_4PI/AAAAAAAAAHg/e3FoTIa3nCg/s1600/06.Console.png)](http://4.bp.blogspot.com/-UwUWUKz-yBQ/UHeJVA0_4PI/AAAAAAAAAHg/e3FoTIa3nCg/s1600/06.Console.png)</div>
<div style="clear: both; text-align: left;">就會打開Console介面</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-jThsTH3PeJw/UHeJVgYOTkI/AAAAAAAAAHk/-sM2w6Ud-H4/s1600/07.Console2.png)](http://1.bp.blogspot.com/-jThsTH3PeJw/UHeJVgYOTkI/AAAAAAAAAHk/-sM2w6Ud-H4/s1600/07.Console2.png)</div>
<div style="clear: both; text-align: left;">還是以JQuery為例
Install-Package是安裝套件
Update-Package是更新套件
參數-Version可以指定版本，如不指定則會以最新版為主
Uninstall-Package是移除套件</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-cdtMPEn5V04/UHeJWvumlQI/AAAAAAAAAHw/J1Ow8bM38kA/s1600/08.Command.png)](http://1.bp.blogspot.com/-cdtMPEn5V04/UHeJWvumlQI/AAAAAAAAAHw/J1Ow8bM38kA/s1600/08.Command.png)</div>
<div style="clear: both; text-align: left;">搜尋套件的命令是Get-Package
參數ListAvailable可以列出可用套件
參數AllVersions用來列出該套件所有版本 
參數Filter用來過慮條件</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-BdqrQE8Fvqg/UHeJXsL6RhI/AAAAAAAAAH0/QsOebdVodSk/s1600/09.Filter.png)](http://4.bp.blogspot.com/-BdqrQE8Fvqg/UHeJXsL6RhI/AAAAAAAAAH0/QsOebdVodSk/s1600/09.Filter.png)</div>
<div style="clear: both; text-align: left;">上一篇:[安裝NuGet套件管理工具](http://blog.developer.idv.tw/2012/10/nuget.html)
下一篇:[架設Nuget.Server](http://blog.developer.idv.tw/2012/10/nugetserver.html)</div>