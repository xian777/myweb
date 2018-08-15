---
title: Jenkins 安裝 MSTest
tags:
  - Jenkins
date: 2015-09-16 16:26:00
---

下載Visual Studio Agents 2015
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-_Umr--V4V3U/VfknYUXoEbI/AAAAAAAAChc/jg6ZNx4qHno/s1600/01.download.png)](http://2.bp.blogspot.com/-_Umr--V4V3U/VfknYUXoEbI/AAAAAAAAChc/jg6ZNx4qHno/s1600/01.download.png)</div>
安裝Visual Studio Agents 2015
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-o1dba2X_Itw/VfknYS7d9DI/AAAAAAAAChI/iPNFXpq_m6Y/s1600/02.install.png)](http://3.bp.blogspot.com/-o1dba2X_Itw/VfknYS7d9DI/AAAAAAAAChI/iPNFXpq_m6Y/s1600/02.install.png)</div>
安裝完後會有MSTest.exe相關的工具
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Wrcu2ooOiVk/VfknYUYTc8I/AAAAAAAACiI/DD6sDL5RquI/s1600/03.MSTest%25E4%25BD%258D%25E7%25BD%25AE.png)](http://3.bp.blogspot.com/-Wrcu2ooOiVk/VfknYUYTc8I/AAAAAAAACiI/DD6sDL5RquI/s1600/03.MSTest%25E4%25BD%258D%25E7%25BD%25AE.png)</div>
安裝MSTest Plugin
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-cS7FjLfzdkk/VfknYxFXtCI/AAAAAAAAChY/cDMNnB4soSs/s1600/04.%25E5%25AE%2589%25E8%25A3%259DPlugin.png)](http://4.bp.blogspot.com/-cS7FjLfzdkk/VfknYxFXtCI/AAAAAAAAChY/cDMNnB4soSs/s1600/04.%25E5%25AE%2589%25E8%25A3%259DPlugin.png)</div>
安裝完成後重新啟動
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-hkTk5p1E13w/VfknZC7en_I/AAAAAAAACiA/IexA64ONuTo/s1600/05.%25E5%25AE%2589%25E8%25A3%259D%25E5%25AE%258C%25E6%2588%2590.png)](http://1.bp.blogspot.com/-hkTk5p1E13w/VfknZC7en_I/AAAAAAAACiA/IexA64ONuTo/s1600/05.%25E5%25AE%2589%25E8%25A3%259D%25E5%25AE%258C%25E6%2588%2590.png)</div>
管理Jenkins =&gt; 設定系統
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-zDvrRK1d7qw/VfknZI3z6NI/AAAAAAAAChs/m8Dw-X8kIdA/s1600/06.%25E8%25A8%25AD%25E5%25AE%259A%25E7%25B3%25BB%25E7%25B5%25B1.png)](http://2.bp.blogspot.com/-zDvrRK1d7qw/VfknZI3z6NI/AAAAAAAAChs/m8Dw-X8kIdA/s1600/06.%25E8%25A8%25AD%25E5%25AE%259A%25E7%25B3%25BB%25E7%25B5%25B1.png)</div>
設定MSTest路徑
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Jm59N2yNC_E/VfknZZ45kxI/AAAAAAAACho/P-Jzgcxe2os/s1600/07.%25E8%25A8%25AD%25E5%25AE%259Amstest%25E8%25B7%25AF%25E5%25BE%2591.png)](http://2.bp.blogspot.com/-Jm59N2yNC_E/VfknZZ45kxI/AAAAAAAACho/P-Jzgcxe2os/s1600/07.%25E8%25A8%25AD%25E5%25AE%259Amstest%25E8%25B7%25AF%25E5%25BE%2591.png)</div>
新增一個測試專案
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-XQhDZ_W8oTc/VfkoEokeDMI/AAAAAAAACiQ/wFpl_Kn8b4M/s1600/08.%25E6%2596%25B0%25E5%25A2%259E%25E6%25B8%25AC%25E8%25A9%25A6%25E5%25B0%2588%25E6%25A1%2588.png)](http://2.bp.blogspot.com/-XQhDZ_W8oTc/VfkoEokeDMI/AAAAAAAACiQ/wFpl_Kn8b4M/s1600/08.%25E6%2596%25B0%25E5%25A2%259E%25E6%25B8%25AC%25E8%25A9%25A6%25E5%25B0%2588%25E6%25A1%2588.png)</div>
新增建置步驟
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Fr-q7s6B_bQ/VfknZ5FPBfI/AAAAAAAACh0/PLWo8-AfeYg/s1600/10.%25E5%258A%25A0%25E5%2585%25A5%25E5%25BB%25BA%25E7%25BD%25AE%25E6%25AD%25A5%25E9%25A9%259F.png)](http://4.bp.blogspot.com/-Fr-q7s6B_bQ/VfknZ5FPBfI/AAAAAAAACh0/PLWo8-AfeYg/s1600/10.%25E5%258A%25A0%25E5%2585%25A5%25E5%25BB%25BA%25E7%25BD%25AE%25E6%25AD%25A5%25E9%25A9%259F.png)</div>
新增建置後動作
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-HReseVBcVUQ/VfknZ3YVOVI/AAAAAAAACh4/uRvenG4XGkE/s1600/11.%25E5%258A%25A0%25E5%2585%25A5%25E5%25BB%25BA%25E7%25BD%25AE%25E5%25BE%258C%25E5%258B%2595%25E4%25BD%259C.png)](http://4.bp.blogspot.com/-HReseVBcVUQ/VfknZ3YVOVI/AAAAAAAACh4/uRvenG4XGkE/s1600/11.%25E5%258A%25A0%25E5%2585%25A5%25E5%25BB%25BA%25E7%25BD%25AE%25E5%25BE%258C%25E5%258B%2595%25E4%25BD%259C.png)</div>
建置結果
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-KseROb3JgPw/VfknaYvMDRI/AAAAAAAACiE/xbSa9gSLp-M/s1600/12.%25E5%25BB%25BA%25E7%25BD%25AE%25E7%25B5%2590%25E6%259E%259C.png)](http://4.bp.blogspot.com/-KseROb3JgPw/VfknaYvMDRI/AAAAAAAACiE/xbSa9gSLp-M/s1600/12.%25E5%25BB%25BA%25E7%25BD%25AE%25E7%25B5%2590%25E6%259E%259C.png)</div>