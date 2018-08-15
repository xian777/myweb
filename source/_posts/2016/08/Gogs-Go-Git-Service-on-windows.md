---
title: Gogs - Go Git Service on windows
tags:
  - git
  - gogs
date: 2016-08-14 15:47:00
---

先到[官網](https://gogs.io/)下載windodws版本編譯好的二進制壓縮檔
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-gdi57inFIN4/V7AhnC2PX4I/AAAAAAAAD0k/XeoXDAuNKfs_POtQf4RctzGK2Or6zipHgCLcB/s1600/01.png)](https://4.bp.blogspot.com/-gdi57inFIN4/V7AhnC2PX4I/AAAAAAAAD0k/XeoXDAuNKfs_POtQf4RctzGK2Or6zipHgCLcB/s1600/01.png)</div>
解壓縮後到資料夾下執行gogs web即可，預設Listen port是3000
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-hslHcwh_lgw/V7AhnCfwnZI/AAAAAAAAD0g/e2HASIhkOLE4DP3i8_Fw3a3ANPvQ6yV6ACLcB/s1600/02.png)](https://1.bp.blogspot.com/-hslHcwh_lgw/V7AhnCfwnZI/AAAAAAAAD0g/e2HASIhkOLE4DP3i8_Fw3a3ANPvQ6yV6ACLcB/s1600/02.png)</div>
打開瀏覽器進入http://127.0.0.1:3000後，開始初始化設定
設定要使用的資料庫和專案放置的資料夾路徑
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-gsVP-BbXeHU/V7AhnAcVd3I/AAAAAAAAD0o/uRGkeqy8i3IcQj9jgrDQdwA0myitxAfdQCLcB/s1600/03.png)](https://3.bp.blogspot.com/-gsVP-BbXeHU/V7AhnAcVd3I/AAAAAAAAD0o/uRGkeqy8i3IcQj9jgrDQdwA0myitxAfdQCLcB/s1600/03.png)</div>

勾選禁止註冊和登錄訪問限制
再建立一個管理員帳號就完成設定了
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-u7QiBsg5pLw/V7AhnqGtO3I/AAAAAAAAD0s/rUxLIbIVUc00pqi0RrHaysQd49CvC7q4ACLcB/s1600/04.png)](https://4.bp.blogspot.com/-u7QiBsg5pLw/V7AhnqGtO3I/AAAAAAAAD0s/rUxLIbIVUc00pqi0RrHaysQd49CvC7q4ACLcB/s1600/04.png)</div>
如果沒有勾選禁止註冊，右上角的登入旁邊就會有一個註冊的功能
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-4b9TPMqjwrw/V7AjGbhqG8I/AAAAAAAAD1g/iG5ub2HARlEeOy69gRHafkMLV5-MgcatwCLcB/s1600/05.png)](https://4.bp.blogspot.com/-4b9TPMqjwrw/V7AjGbhqG8I/AAAAAAAAD1g/iG5ub2HARlEeOy69gRHafkMLV5-MgcatwCLcB/s1600/05.png)</div>

登入後先來建一個專案
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-IoZIbfFg2ug/V7AhnhNObGI/AAAAAAAAD0w/VRZTy9g_7F4DCiLyI0cjwhZ-chrPAevSwCLcB/s1600/06.png)](https://2.bp.blogspot.com/-IoZIbfFg2ug/V7AhnhNObGI/AAAAAAAAD0w/VRZTy9g_7F4DCiLyI0cjwhZ-chrPAevSwCLcB/s1600/06.png)</div>

輸入專案的名稱，把可見度勾成私有的，就必需有帳密才能下載專案
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-UpeLRN8U0PE/V7Ahn9MCkUI/AAAAAAAAD04/exwpySFk3e04-KQUhzyGOvuSOUUhwfz2ACLcB/s1600/07.png)](https://1.bp.blogspot.com/-UpeLRN8U0PE/V7Ahn9MCkUI/AAAAAAAAD04/exwpySFk3e04-KQUhzyGOvuSOUUhwfz2ACLcB/s1600/07.png)</div>
右上角的路徑是當初設定時所輸入的網址
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-FnJ590Dnwuk/V7AhoPh1v-I/AAAAAAAAD08/bIq-2UuFjw8fHmDXUErnzk53VZqHL5BNwCLcB/s1600/08.png)](https://1.bp.blogspot.com/-FnJ590Dnwuk/V7AhoPh1v-I/AAAAAAAAD08/bIq-2UuFjw8fHmDXUErnzk53VZqHL5BNwCLcB/s1600/08.png)</div>
把專案取回來
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-8D2dnijW8iU/V7AhoAhuuII/AAAAAAAAD1A/EfiP0lkTnIctqFIg5MYCPJwm2LG0tZDxQCLcB/s1600/09.png)](https://2.bp.blogspot.com/-8D2dnijW8iU/V7AhoAhuuII/AAAAAAAAD1A/EfiP0lkTnIctqFIg5MYCPJwm2LG0tZDxQCLcB/s1600/09.png)</div>
因為是私人專案所以需要輸入帳密
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-oWo36HJO95s/V7AhoYm3wGI/AAAAAAAAD1E/EHmOwTNy4cYps0h42LRlywrzfFZjqNrwgCLcB/s1600/10.png)](https://2.bp.blogspot.com/-oWo36HJO95s/V7AhoYm3wGI/AAAAAAAAD1E/EHmOwTNy4cYps0h42LRlywrzfFZjqNrwgCLcB/s1600/10.png)</div>
新增一個測試專案
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-AAMdPFCFdBs/V7AhoTl8-kI/AAAAAAAAD1I/mkN1UwVRkIYmnoKzJHVDFDWBk8BjI5mDQCLcB/s1600/12.png)](https://2.bp.blogspot.com/-AAMdPFCFdBs/V7AhoTl8-kI/AAAAAAAAD1I/mkN1UwVRkIYmnoKzJHVDFDWBk8BjI5mDQCLcB/s1600/12.png)</div>
把測試專案移到工作目錄後送交
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-_xT0GLgF-_A/V7Ahor84L_I/AAAAAAAAD1M/K1nxBB2GMIASEkmh6bQerNAgNKUIKld_ACLcB/s1600/13.png)](https://2.bp.blogspot.com/-_xT0GLgF-_A/V7Ahor84L_I/AAAAAAAAD1M/K1nxBB2GMIASEkmh6bQerNAgNKUIKld_ACLcB/s1600/13.png)</div>
把測試專案推送到gogs
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-e880ZNeiJGU/V7Ahooi8LkI/AAAAAAAAD1Q/hs5y8jaoI8MkotEQSHFkZ-NwTDhuGKRhwCLcB/s1600/15.png)](https://2.bp.blogspot.com/-e880ZNeiJGU/V7Ahooi8LkI/AAAAAAAAD1Q/hs5y8jaoI8MkotEQSHFkZ-NwTDhuGKRhwCLcB/s1600/15.png)</div>
專案同步完成
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-MIzAkq01Q84/V7Aho156k9I/AAAAAAAAD1U/zIUcvw2GbEA53yuYSPy2YM7gCscPAgZMACLcB/s1600/17.png)](https://1.bp.blogspot.com/-MIzAkq01Q84/V7Aho156k9I/AAAAAAAAD1U/zIUcvw2GbEA53yuYSPy2YM7gCscPAgZMACLcB/s1600/17.png)</div>