---
title: Team Foundation Server 安裝
tags:
  - Team Foundation Server
date: 2014-12-22 16:49:00
---

首先到[Visual Studio的官網](http://www.visualstudio.com/)下載Team Foundation Server 90天免費試用版
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-hxGsZCAur7w/VJfWVNxQwtI/AAAAAAAAB08/TzIPMCI2qps/s1600/01.png)](http://4.bp.blogspot.com/-hxGsZCAur7w/VJfWVNxQwtI/AAAAAAAAB08/TzIPMCI2qps/s1600/01.png)</div>
要安裝的時後雙擊tfs_server.exe就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-A7eVh247ul0/VJfWZ96-FUI/AAAAAAAAB1E/j_r_nc6Z8SY/s1600/02.png)](http://2.bp.blogspot.com/-A7eVh247ul0/VJfWZ96-FUI/AAAAAAAAB1E/j_r_nc6Z8SY/s1600/02.png)</div>
勾選接受授權條款後，點擊立即安裝就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-9z2sc1IX-Kg/VJfWdw4752I/AAAAAAAAB1M/OGwxMcC7-gk/s1600/03.png)](http://2.bp.blogspot.com/-9z2sc1IX-Kg/VJfWdw4752I/AAAAAAAAB1M/OGwxMcC7-gk/s1600/03.png)</div>
接下來就會開始跑安裝流程
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-cqjSmTcP2ss/VJfXrtx3QNI/AAAAAAAAB1Y/HprxZDpDfeM/s1600/04.%E5%AE%89%E8%A3%9D%E4%B8%AD.png)](http://1.bp.blogspot.com/-cqjSmTcP2ss/VJfXrtx3QNI/AAAAAAAAB1Y/HprxZDpDfeM/s1600/04.%E5%AE%89%E8%A3%9D%E4%B8%AD.png)</div>
安裝成功後會跳出授權畫面，安裝試用版授權會有90天的試用期
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-DD02x-xmYI0/VJfYbirgJJI/AAAAAAAAB1g/FlmFAefZysw/s1600/05.%E6%8E%88%E6%AC%8A.png)](http://3.bp.blogspot.com/-DD02x-xmYI0/VJfYbirgJJI/AAAAAAAAB1g/FlmFAefZysw/s1600/05.%E6%8E%88%E6%AC%8A.png)</div>
接下來就是在組態中心選擇適合自已環境的設定
Team Foundation Application Server可以選擇幾種層級
基本：自動在本機安裝SQL 2012 Express版本並使用
[標準單一伺服器](http://msdn.microsoft.com/zh-tw/library/vstudio/dd631903.aspx)：需自行安裝SQL Server 2008 R2以上的版本，再透過這個精靈來設定
[進階](http://msdn.microsoft.com/zh-tw/library/vstudio/dd631919.aspx)：SQL Server裝到另外一台機器上面，再用這個精靈來設定
僅限應用程式層：做伺服器陣列的時後，再選這個精靈來設定

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ETId2vPV8uM/VJfYx90Or7I/AAAAAAAAB1o/SJUzKalZ4Ok/s1600/06.%E7%B5%84%E6%85%8B%E4%B8%AD%E5%BF%83.png)](http://2.bp.blogspot.com/-ETId2vPV8uM/VJfYx90Or7I/AAAAAAAAB1o/SJUzKalZ4Ok/s1600/06.%E7%B5%84%E6%85%8B%E4%B8%AD%E5%BF%83.png)</div>
管理主控台可以做更多的設定
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-xBpczMPsD4w/VJfZR7lSB5I/AAAAAAAAB10/S-_XFmyNdT8/s1600/07.%E7%AE%A1%E7%90%86%E4%B8%BB%E6%8E%A7%E5%8F%B0.png)](http://3.bp.blogspot.com/-xBpczMPsD4w/VJfZR7lSB5I/AAAAAAAAB10/S-_XFmyNdT8/s1600/07.%E7%AE%A1%E7%90%86%E4%B8%BB%E6%8E%A7%E5%8F%B0.png)</div>