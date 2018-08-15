---
title: 架設NuPeek Symbol & NuGet Server
tags:
  - NuGet
  - Symbol
date: 2015-08-07 14:47:00
---

首先到Bitbucket下載NuPeek的原始碼回來
[https://bitbucket.org/thinkbeforecoding/nupeek](https://bitbucket.org/thinkbeforecoding/nupeek)
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-oQRiidn7woQ/VcRUEOkTHzI/AAAAAAAACYs/6-EfBRJj5dk/s1600/01.%25E5%25AE%2598%25E7%25B6%25B2%25E4%25B8%258B%25E8%25BC%2589.png)](http://2.bp.blogspot.com/-oQRiidn7woQ/VcRUEOkTHzI/AAAAAAAACYs/6-EfBRJj5dk/s1600/01.%25E5%25AE%2598%25E7%25B6%25B2%25E4%25B8%258B%25E8%25BC%2589.png)</div>
打開專案後，記得先改一下Symbols資料夾的名稱，不然會卡住
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-PR8hHSy2T8k/VcRUELObHvI/AAAAAAAACYk/3nHRJakSjWI/s1600/02.%25E6%259B%25B4%25E5%2590%258D%25E8%25B3%2587%25E6%2596%2599%25E5%25A4%25BE.png)](http://2.bp.blogspot.com/-PR8hHSy2T8k/VcRUELObHvI/AAAAAAAACYk/3nHRJakSjWI/s1600/02.%25E6%259B%25B4%25E5%2590%258D%25E8%25B3%2587%25E6%2596%2599%25E5%25A4%25BE.png)</div>
web.config中，也要把symbolsPath的值改成修改後的名稱
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-SE4iQc3tiRk/VcRUEOVlHII/AAAAAAAACYo/iyVluHcVMbs/s1600/03.%25E6%259B%25B4%25E6%2594%25B9%25E8%25A8%25AD%25E5%25AE%259A%25E6%25AA%2594.png)](http://1.bp.blogspot.com/-SE4iQc3tiRk/VcRUEOVlHII/AAAAAAAACYo/iyVluHcVMbs/s1600/03.%25E6%259B%25B4%25E6%2594%25B9%25E8%25A8%25AD%25E5%25AE%259A%25E6%25AA%2594.png)</div>
佈署的Server後，首頁會有相關的資訊
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-N2dx5rrJZoA/VcRUEg5yZvI/AAAAAAAACYw/3ngpW204hMU/s1600/04.%25E9%25A6%2596%25E9%25A0%2581.png)](http://1.bp.blogspot.com/-N2dx5rrJZoA/VcRUEg5yZvI/AAAAAAAACYw/3ngpW204hMU/s1600/04.%25E9%25A6%2596%25E9%25A0%2581.png)</div>
在Visual Studio中的工具-&gt;選項-&gt;偵錯-&gt;一般，改用來源伺服器支援
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-2E822hTBCzA/VcRUEyZbAUI/AAAAAAAACY8/63nyAVu3Oqw/s1600/05.%25E4%25BE%2586%25E6%25BA%2590%25E4%25BC%25BA%25E6%259C%258D%25E5%2599%25A8.png)](http://2.bp.blogspot.com/-2E822hTBCzA/VcRUEyZbAUI/AAAAAAAACY8/63nyAVu3Oqw/s1600/05.%25E4%25BE%2586%25E6%25BA%2590%25E4%25BC%25BA%25E6%259C%258D%25E5%2599%25A8.png)</div>
在Visual Studio中的工具-&gt;選項-&gt;偵錯-&gt;符號，新增SymbolServer位置
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-171ZsRPe9fA/VcRUE5-ZggI/AAAAAAAACY4/r4f_T4B9vko/s1600/06.%25E8%25A8%25AD%25E5%25AE%259Asymbol.png)](http://1.bp.blogspot.com/-171ZsRPe9fA/VcRUE5-ZggI/AAAAAAAACY4/r4f_T4B9vko/s1600/06.%25E8%25A8%25AD%25E5%25AE%259Asymbol.png)</div>
Symbol推送到NuPeek後，在程式碼中下個中斷點
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-tjJyCp9Z_Y0/VcRUFN0nfJI/AAAAAAAACZA/CsERo4TzUNs/s1600/07.%25E4%25B8%25AD%25E6%2596%25B7%25E9%25BB%259E.png)](http://1.bp.blogspot.com/-tjJyCp9Z_Y0/VcRUFN0nfJI/AAAAAAAACZA/CsERo4TzUNs/s1600/07.%25E4%25B8%25AD%25E6%2596%25B7%25E9%25BB%259E.png)</div>
透過Fillder可以看到下載Symbol符號和Source
符號快取資料夾中也可以看到下載的資料
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-YoZEmEC8L_M/VcRUFr50hMI/AAAAAAAACZE/r4Cm7K-fVFE/s1600/08.%25E4%25B8%258B%25E8%25BC%2589%25E7%25AC%25A6%25E8%2599%259F.png)](http://1.bp.blogspot.com/-YoZEmEC8L_M/VcRUFr50hMI/AAAAAAAACZE/r4Cm7K-fVFE/s1600/08.%25E4%25B8%258B%25E8%25BC%2589%25E7%25AC%25A6%25E8%2599%259F.png)</div>
F11進入函式後，可以看到符號的Source是在符號快取資料夾中取得
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-4S1fUEVs4aM/VcRUF1oPMJI/AAAAAAAACZg/gzltljDWqUY/s1600/09.%25E9%2580%25B2%25E5%2585%25A5%25E4%25B8%25AD%25E6%2596%25B7%25E9%25BB%259E.png)](http://2.bp.blogspot.com/-4S1fUEVs4aM/VcRUF1oPMJI/AAAAAAAACZg/gzltljDWqUY/s1600/09.%25E9%2580%25B2%25E5%2585%25A5%25E4%25B8%25AD%25E6%2596%25B7%25E9%25BB%259E.png)</div>