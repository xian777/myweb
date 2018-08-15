---
title: Gogs with application request routing
tags:
  - arr
  - gogs
date: 2016-08-15 23:14:00
---

Application Request Route的使用方式可以參考以前的筆記
[透過Application Request Route來做SSL offloading](http://blog.developer.idv.tw/2016/05/application-request-routessl-offloading_8.html)
[http://blog.developer.idv.tw/2016/05/application-request-routessl-offloading_8.html](http://blog.developer.idv.tw/2016/05/application-request-routessl-offloading_8.html)

預設的站台只繫結http 80 port
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-RTDUH6_NBvI/V7HcIB-tOFI/AAAAAAAAD3I/0SxH-OjlwCkC20MVjaMgHZ55V6XCFHh5ACLcB/s1600/01.png)](https://1.bp.blogspot.com/-RTDUH6_NBvI/V7HcIB-tOFI/AAAAAAAAD3I/0SxH-OjlwCkC20MVjaMgHZ55V6XCFHh5ACLcB/s1600/01.png)</div>
安裝好ARR後，新增一組Server Farm
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-BUQI0vG1O2s/V7HcIGM-NCI/AAAAAAAAD3Q/BDTR_cOmalMu9JgL8HD8LgMDYTWZDuwNgCLcB/s1600/02.png)](https://4.bp.blogspot.com/-BUQI0vG1O2s/V7HcIGM-NCI/AAAAAAAAD3Q/BDTR_cOmalMu9JgL8HD8LgMDYTWZDuwNgCLcB/s1600/02.png)</div>
新增一台伺服器，httpPort改成3000
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-2iQGlC2nMUE/V7HcIBCzN4I/AAAAAAAAD3M/63hu2Ct49McJocI0wdU0YEg7XDHIX0vywCLcB/s1600/03.png)](https://2.bp.blogspot.com/-2iQGlC2nMUE/V7HcIBCzN4I/AAAAAAAAD3M/63hu2Ct49McJocI0wdU0YEg7XDHIX0vywCLcB/s1600/03.png)</div>
新增一條URL Rewrite規則
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-X64dGenYaKM/V7HcIY_tM7I/AAAAAAAAD3U/9lFevWOGQigbzFaZDbi-dTq_R9GTgskzACLcB/s1600/04.png)](https://4.bp.blogspot.com/-X64dGenYaKM/V7HcIY_tM7I/AAAAAAAAD3U/9lFevWOGQigbzFaZDbi-dTq_R9GTgskzACLcB/s1600/04.png)</div>
使用規則運算式: .*
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-FD4P_AUW1x8/V7HcIpYTCnI/AAAAAAAAD3Y/NlDxlJt4rcAYefwLWIFOugguupLnjwixACLcB/s1600/05.png)](https://1.bp.blogspot.com/-FD4P_AUW1x8/V7HcIpYTCnI/AAAAAAAAD3Y/NlDxlJt4rcAYefwLWIFOugguupLnjwixACLcB/s1600/05.png)</div>
路由到剛設定的伺服器陣列
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-03Fe7Z8Vc0M/V7HcIrI03dI/AAAAAAAAD3c/0gO3EuOxOJMoXDxkSnPkEZbyiUtTa8WjgCLcB/s1600/06.png)](https://1.bp.blogspot.com/-03Fe7Z8Vc0M/V7HcIrI03dI/AAAAAAAAD3c/0gO3EuOxOJMoXDxkSnPkEZbyiUtTa8WjgCLcB/s1600/06.png)</div>
新增一組測試網址
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-PMDL1lmoQkI/V7HcI264_DI/AAAAAAAAD3g/IhKetCNMxBwnF3MMbHKU59mP2LlCno4jACLcB/s1600/07.png)](https://3.bp.blogspot.com/-PMDL1lmoQkI/V7HcI264_DI/AAAAAAAAD3g/IhKetCNMxBwnF3MMbHKU59mP2LlCno4jACLcB/s1600/07.png)</div>
瀏覽測試網址，http port 80 會路由到gogs的port 3000
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-cBz_me155kY/V7HcJMSQtdI/AAAAAAAAD3k/jDB8V0C-uhkXo2o_0WjMDq-otZYSGDblQCLcB/s1600/08.png)](https://2.bp.blogspot.com/-cBz_me155kY/V7HcJMSQtdI/AAAAAAAAD3k/jDB8V0C-uhkXo2o_0WjMDq-otZYSGDblQCLcB/s1600/08.png)</div>