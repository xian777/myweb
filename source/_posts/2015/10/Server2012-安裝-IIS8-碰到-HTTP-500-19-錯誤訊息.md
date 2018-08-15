---
title: Server2012 安裝 IIS8 碰到 HTTP 500.19 錯誤訊息
tags:
  - iis
date: 2015-10-09 11:18:00
---

開始使用Server2012R2上面的IIS 8，結果就碰到一個問題500.19的問題
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-FGSmEdeARrs/VhczqkuRogI/AAAAAAAACkQ/FGrIdc6JyDs/s1600/00.500.19.png)](http://4.bp.blogspot.com/-FGSmEdeARrs/VhczqkuRogI/AAAAAAAACkQ/FGrIdc6JyDs/s1600/00.500.19.png)</div>
以為是權限問題，搞了半天，錯誤訊息又變成設定檔錯誤
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-r7oRQE18Dm4/VhczIgXuuUI/AAAAAAAACkI/_oZ6irWnsBE/s1600/00.error.png)](http://1.bp.blogspot.com/-r7oRQE18Dm4/VhczIgXuuUI/AAAAAAAACkI/_oZ6irWnsBE/s1600/00.error.png)</div>

爬文發現是ASP.NET的模組沒裝好，最簡單的方法就是aspnet_regiis -i重新安裝就好
但在Server2012 R2上面已經不再支援這個命令了...
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ff_xTkXmelA/VhcxtKP1XkI/AAAAAAAACiw/t8oNHmYaIZ0/s1600/00.regiis.png)](http://2.bp.blogspot.com/-ff_xTkXmelA/VhcxtKP1XkI/AAAAAAAACiw/t8oNHmYaIZ0/s1600/00.regiis.png)</div>
只好打開新增角色和精靈來研究一下IIS的功能模組
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-1Dg6QD8BVRY/VhcxtJYIalI/AAAAAAAACis/qWtmPwkXB40/s1600/01.%25E6%2596%25B0%25E5%25A2%259E%25E8%25A7%2592%25E8%2589%25B2.png)](http://2.bp.blogspot.com/-1Dg6QD8BVRY/VhcxtJYIalI/AAAAAAAACis/qWtmPwkXB40/s1600/01.%25E6%2596%25B0%25E5%25A2%259E%25E8%25A7%2592%25E8%2589%25B2.png)</div>
選擇角色型或功能型安裝
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Zqp7wZ6mYbY/VhcxtMAW1iI/AAAAAAAACio/Xo1WFEaPVVE/s1600/02.%25E8%25A7%2592%25E8%2589%25B2%25E5%259E%258B%25E5%25AE%2589%25E8%25A3%259D.png)](http://2.bp.blogspot.com/-Zqp7wZ6mYbY/VhcxtMAW1iI/AAAAAAAACio/Xo1WFEaPVVE/s1600/02.%25E8%25A7%2592%25E8%2589%25B2%25E5%259E%258B%25E5%25AE%2589%25E8%25A3%259D.png)</div>
選擇伺服器
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-vkF7mkt1Ntk/VhcxtlxKmZI/AAAAAAAACi0/yESQb9cuZd0/s1600/03.%25E4%25BC%25BA%25E6%259C%258D%25E5%2599%25A8%25E9%25A0%2585%25E7%259B%25AE.png)](http://1.bp.blogspot.com/-vkF7mkt1Ntk/VhcxtlxKmZI/AAAAAAAACi0/yESQb9cuZd0/s1600/03.%25E4%25BC%25BA%25E6%259C%258D%25E5%2599%25A8%25E9%25A0%2585%25E7%259B%25AE.png)</div>
勾選網頁伺服器(IIS)和應用程式伺服器
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-wldIGTpf1To/Vhcxt2WIH2I/AAAAAAAACjQ/xYoqS5S8cyM/s1600/04.%25E4%25BC%25BA%25E6%259C%258D%25E5%2599%25A8%25E8%25A7%2592%25E8%2589%25B2.png)](http://4.bp.blogspot.com/-wldIGTpf1To/Vhcxt2WIH2I/AAAAAAAACjQ/xYoqS5S8cyM/s1600/04.%25E4%25BC%25BA%25E6%259C%258D%25E5%2599%25A8%25E8%25A7%2592%25E8%2589%25B2.png)</div>
勾選ASP.NET45功能模組
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-8WrAFc3_vUo/Vhcxt7DlS5I/AAAAAAAACjA/wlc6DwnsYYI/s1600/05.asp45.png)](http://4.bp.blogspot.com/-8WrAFc3_vUo/Vhcxt7DlS5I/AAAAAAAACjA/wlc6DwnsYYI/s1600/05.asp45.png)</div>
網頁伺服器(IIS)的角色服務中，勾選ASP.NET4.5
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-j_BGR9TPWQs/VhcyoH_ckII/AAAAAAAACj4/M2jDUV5NMXI/s1600/06.asp45.png)](http://2.bp.blogspot.com/-j_BGR9TPWQs/VhcyoH_ckII/AAAAAAAACj4/M2jDUV5NMXI/s1600/06.asp45.png)</div>
應用程式伺服器的角色服務中，勾選網頁伺服器(IIS)支援
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-vdp2raIVtXg/VhcysyVo-iI/AAAAAAAACkA/Ms8uKV9j0zc/s1600/07.iis.png)](http://3.bp.blogspot.com/-vdp2raIVtXg/VhcysyVo-iI/AAAAAAAACkA/Ms8uKV9j0zc/s1600/07.iis.png)</div>
準備安裝
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-i4v0KRMe7FM/VhcxutX6UWI/AAAAAAAACjY/_-3X6U_LuZg/s1600/08.install.png)](http://2.bp.blogspot.com/-i4v0KRMe7FM/VhcxutX6UWI/AAAAAAAACjY/_-3X6U_LuZg/s1600/08.install.png)</div>
打完收工