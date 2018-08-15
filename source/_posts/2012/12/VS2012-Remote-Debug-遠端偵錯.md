---
title: VS2012 Remote Debug 遠端偵錯
tags:
  - Remote Debug
  - 遠端偵錯
date: 2012-12-25 12:03:00
---

<div class="separator" style="clear: both; text-align: left;">VS2012的遠端偵錯變的簡單多了，不再需要驗證身份就可以使用，但相對的作業系統需要更新到Server2008R2以上 </div>
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-lQq_Fp2n3AE/UNkege7WrMI/AAAAAAAAAjU/bjY8oAEdBfQ/s1600/VS2012RemoteDebug.png)](http://4.bp.blogspot.com/-lQq_Fp2n3AE/UNkege7WrMI/AAAAAAAAAjU/bjY8oAEdBfQ/s1600/VS2012RemoteDebug.png)</div><div class="separator" style="clear: both; text-align: left;">首先下載Remote Tools for Visual Studio 2012</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-VqG02LMi9aE/UNkerTlrF5I/AAAAAAAAAjc/HxWTX18lW5w/s1600/01.Download.png)](http://2.bp.blogspot.com/-VqG02LMi9aE/UNkerTlrF5I/AAAAAAAAAjc/HxWTX18lW5w/s1600/01.Download.png)</div><div class="separator" style="clear: both; text-align: left;">在伺服器上面安裝遠端偵錯工具 </div>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-N2cnZ2-rzqM/UNkgRPNpyRI/AAAAAAAAAkE/4bLI0GskB50/s1600/02.InstallUI.png)](http://3.bp.blogspot.com/-N2cnZ2-rzqM/UNkgRPNpyRI/AAAAAAAAAkE/4bLI0GskB50/s1600/02.InstallUI.png)</div><div class="separator" style="clear: both; text-align: left;">在Server上安裝好遠端偵錯工具後，打開遠端偵錯工具</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-ttJKtFGuWWY/UNkk8TCKtZI/AAAAAAAAAk8/d-NO1x5AcVg/s1600/03.Start.png)](http://1.bp.blogspot.com/-ttJKtFGuWWY/UNkk8TCKtZI/AAAAAAAAAk8/d-NO1x5AcVg/s1600/03.Start.png)</div>
<div class="separator" style="clear: both; text-align: left;">設定成非驗證模式，允許任何使用者執行偵錯，和延長閒置時間</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-7wjO-1g8oRg/UNkkyfqDIuI/AAAAAAAAAk0/HeaygtT76r8/s1600/04.Connect.png)](http://3.bp.blogspot.com/-7wjO-1g8oRg/UNkkyfqDIuI/AAAAAAAAAk0/HeaygtT76r8/s1600/04.Connect.png)</div><div class="separator" style="clear: both; text-align: left;">
</div>打開VS2012，附加執行緒，選擇遠端(非驗證)，輸入IP和Port號，找到執行檔附加即可
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-umj_9g07B-w/UNklLCMLIDI/AAAAAAAAAlE/-j_M1y-EV7I/s1600/05.Attach.png)](http://4.bp.blogspot.com/-umj_9g07B-w/UNklLCMLIDI/AAAAAAAAAlE/-j_M1y-EV7I/s1600/05.Attach.png)</div>
<div class="separator" style="clear: both; text-align: left;">上一篇: [VS2010 Remote Debug 遠端偵錯](http://blog.developer.idv.tw/2012/09/aspnet.html)</div>