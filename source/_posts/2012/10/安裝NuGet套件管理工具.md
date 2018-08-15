---
title: 安裝NuGet套件管理工具
tags:
  - NuGet
date: 2012-10-11 18:07:00
---

NuGet是.NET平台上面的套件管理工具，主要用來安裝、更新、移除套件，套件中可能包含要參考的元件、使用的資料夾或檔案、設定檔、元件相依性等等，可以幫助我們省下不少時間和繁雜的工作

[http://nuget.codeplex.com](http://nuget.codeplex.com/)
這裡有Source Code和其他的工具

[http://docs.nuget.org/](http://docs.nuget.org/)
這裡有相關的文件 
<div class="separator" style="clear: both; text-align: center;"></div>
<div class="separator" style="clear: both; text-align: left;">先安裝Vistual Studio Extension，選擇工具裡面的擴充功能和更新&nbsp;</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-MUeMfNZgLEg/UHZ6DAcHfuI/AAAAAAAAAEw/UehHNPObctY/s1600/01.Install.png)](http://4.bp.blogspot.com/-MUeMfNZgLEg/UHZ6DAcHfuI/AAAAAAAAAEw/UehHNPObctY/s1600/01.Install.png)</div>
<div class="separator" style="clear: both; text-align: left;">選擇線上Visual Studio 組件庫，第一個就是NuGet Package Manager </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-T7tnB9XcbNE/UHZ6EOMz2EI/AAAAAAAAAE0/-xcg-R3x_eA/s1600/02.NuGet.png)](http://1.bp.blogspot.com/-T7tnB9XcbNE/UHZ6EOMz2EI/AAAAAAAAAE0/-xcg-R3x_eA/s1600/02.NuGet.png)</div><div class="separator" style="clear: both; text-align: left;">點擊下載就可以了</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-NZidbhMyTW8/UHZ6E9eXTfI/AAAAAAAAAE8/m_dEbkwiG_o/s1600/03.download.png)](http://4.bp.blogspot.com/-NZidbhMyTW8/UHZ6E9eXTfI/AAAAAAAAAE8/m_dEbkwiG_o/s1600/03.download.png)</div>
<div class="separator" style="clear: both; text-align: left;">下載後會先跳出授權條款，選擇要安裝擴充功能的產品後按安裝 </div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-skigye0-uG8/UHZ6Fr3kPrI/AAAAAAAAAFE/sGnL5qxDLiU/s1600/04.Licenes.png)](http://3.bp.blogspot.com/-skigye0-uG8/UHZ6Fr3kPrI/AAAAAAAAAFE/sGnL5qxDLiU/s1600/04.Licenes.png)</div>
<div class="separator" style="clear: both; text-align: left;">安裝中... </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-fsigQj-SZXM/UHZ6GjGapHI/AAAAAAAAAFM/rcLavJDcF0M/s1600/05.Install.png)](http://1.bp.blogspot.com/-fsigQj-SZXM/UHZ6GjGapHI/AAAAAAAAAFM/rcLavJDcF0M/s1600/05.Install.png)</div>
<div class="separator" style="clear: both; text-align: left;">安裝完成... </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-DqosQ9bRxm8/UHZ6HYBlntI/AAAAAAAAAFU/fX9zzRxkHno/s1600/06.OK.png)](http://1.bp.blogspot.com/-DqosQ9bRxm8/UHZ6HYBlntI/AAAAAAAAAFU/fX9zzRxkHno/s1600/06.OK.png)</div>
<div class="separator" style="clear: both; text-align: left;">安裝完後需要重新啟動Vistual Studio，按下「立即重新啟動」就好了 </div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-K2YO0NkYsRk/UHZ6IGHGkqI/AAAAAAAAAFg/NR6v74YiUJo/s1600/07.Msg.png)](http://2.bp.blogspot.com/-K2YO0NkYsRk/UHZ6IGHGkqI/AAAAAAAAAFg/NR6v74YiUJo/s1600/07.Msg.png)</div>
<div class="separator" style="clear: both; text-align: left;">重新啟動後，在工具中就會多了一個程式庫套件管理員 </div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-UFABkchM5Pw/UHZ6JNR9PbI/AAAAAAAAAFk/4Ts5mrE1FdM/s1600/07.toolbar.png)](http://4.bp.blogspot.com/-UFABkchM5Pw/UHZ6JNR9PbI/AAAAAAAAAFk/4Ts5mrE1FdM/s1600/07.toolbar.png)</div>
<div class="separator" style="clear: both; text-align: left;">也可以在專案中的參考上按右鍵，選擇管理NuGet套件 </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-1KGwG2VZIpw/UHZ6J8J0IsI/AAAAAAAAAFs/iepvy0TOAgw/s1600/08.toolbar2.png)](http://1.bp.blogspot.com/-1KGwG2VZIpw/UHZ6J8J0IsI/AAAAAAAAAFs/iepvy0TOAgw/s1600/08.toolbar2.png)</div>
<div class="separator" style="clear: both; text-align: left;">選擇要安裝的套件，以JQuery為例 </div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-il5IZubxn0Q/UHeERNvfOsI/AAAAAAAAAGw/zE7t9a1OsKU/s1600/02.install.png)](http://1.bp.blogspot.com/-il5IZubxn0Q/UHeERNvfOsI/AAAAAAAAAGw/zE7t9a1OsKU/s1600/02.install.png)</div>
<div class="separator" style="clear: both; text-align: left;">按下下載後就會開始安裝該套件相關的檔案 </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-JfubxHCmqiM/UHeETIUq3RI/AAAAAAAAAG4/ZmOCOd0Isfg/s1600/03.InstallOK.png)](http://1.bp.blogspot.com/-JfubxHCmqiM/UHeETIUq3RI/AAAAAAAAAG4/ZmOCOd0Isfg/s1600/03.InstallOK.png)</div><div class="separator" style="clear: both; text-align: center;"></div>
<div class="separator" style="clear: both; text-align: left;">安裝後的樣子</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-NWG262i6zjk/UHaD66BbQKI/AAAAAAAAAGc/NRUS0g96X2o/s1600/11.installOK.png)](http://3.bp.blogspot.com/-NWG262i6zjk/UHaD66BbQKI/AAAAAAAAAGc/NRUS0g96X2o/s1600/11.installOK.png)</div><div class="separator" style="clear: both; text-align: left;">
</div>下一篇:[使用NuGet安裝、移除、更新套件](http://blog.developer.idv.tw/2012/10/nuget_12.html)
<div class="separator" style="clear: both; text-align: center;">[
](http://1.bp.blogspot.com/-p47A6-zxV-c/UHZ6Muyt29I/AAAAAAAAAGE/wgMY4e3EiEI/s1600/11.installOK.png)</div>