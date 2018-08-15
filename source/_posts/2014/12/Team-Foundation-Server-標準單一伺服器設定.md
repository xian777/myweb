---
title: Team Foundation Server 標準單一伺服器設定
tags:
  - Team Foundation Server
date: 2014-12-22 18:57:00
---

Team Foundation Server的幾種設定中，基本設字使用的是本機的SQL 2012 Express，所以功能比較少一點
這邊用標準設定來當例子，在開始使用這個組態精靈之前，需要先準備好SQL Server
執行環境需要網域帳號，並選取需要的服務Reporint Service、Analysis Service和全文檢索
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-6_Z1vfAcISE/VJf3O7wq8_I/AAAAAAAAB2U/4re5mgi6iGI/s1600/01.SQL%E5%85%83%E4%BB%B6.png)](http://4.bp.blogspot.com/-6_Z1vfAcISE/VJf3O7wq8_I/AAAAAAAAB2U/4re5mgi6iGI/s1600/01.SQL%E5%85%83%E4%BB%B6.png)</div>
在組態中心中選擇標準單一伺服器
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-R0seRNlWFd0/VJf3ah4KhtI/AAAAAAAAB2c/75dqoIxRaZk/s1600/02.%E7%B5%84%E6%85%8B%E4%B8%AD%E5%BF%83.png)](http://1.bp.blogspot.com/-R0seRNlWFd0/VJf3ah4KhtI/AAAAAAAAB2c/75dqoIxRaZk/s1600/02.%E7%B5%84%E6%85%8B%E4%B8%AD%E5%BF%83.png)</div>
標準組態精靈的歡迎畫面
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-FXLDan8lgbw/VJf3eFi5puI/AAAAAAAAB2k/IPRd3ZsoCtA/s1600/03.%E6%AD%A1%E8%BF%8E%E7%95%AB%E9%9D%A2.png)](http://1.bp.blogspot.com/-FXLDan8lgbw/VJf3eFi5puI/AAAAAAAAB2k/IPRd3ZsoCtA/s1600/03.%E6%AD%A1%E8%BF%8E%E7%95%AB%E9%9D%A2.png)</div>
輸入要用於SharePoint和SQL Server reporting Services的服務帳號
使用一個網域帳號，並且需要是這幾個服務機器上面的本機管理員群組
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-5KI5mPkqDN8/VJf3hmP2kiI/AAAAAAAAB2s/RS6ZgzXhJmE/s1600/04.%E7%B6%B2%E5%9F%9F%E5%B8%B3%E8%99%9F.png)](http://4.bp.blogspot.com/-5KI5mPkqDN8/VJf3hmP2kiI/AAAAAAAAB2s/RS6ZgzXhJmE/s1600/04.%E7%B6%B2%E5%9F%9F%E5%B8%B3%E8%99%9F.png)</div>
這邊可以選擇是否要安裝SharePoint，如果安裝在同一台的話需要的硬體規格比較高，這邊先跳過去
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-sfWfclEOVZA/VJf3lMjEdfI/AAAAAAAAB20/VmYIYNEZ0uA/s1600/05.SharePoint.png)](http://3.bp.blogspot.com/-sfWfclEOVZA/VJf3lMjEdfI/AAAAAAAAB20/VmYIYNEZ0uA/s1600/05.SharePoint.png)</div>
確認組態設定的畫面
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-2cSUVrdSmkE/VJf3xocSm6I/AAAAAAAAB28/8fEtiP1RFXY/s1600/06.%E9%A9%97%E8%AD%89.png)](http://2.bp.blogspot.com/-2cSUVrdSmkE/VJf3xocSm6I/AAAAAAAAB28/8fEtiP1RFXY/s1600/06.%E9%A9%97%E8%AD%89.png)</div>
驗證成功的畫面，接下來按下設定就會開始把需要的功能都設定好
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-laqe8AMezMI/VJf31N1KURI/AAAAAAAAB3E/SuOKkukXWII/s1600/07.%E8%A8%AD%E5%AE%9A.png)](http://4.bp.blogspot.com/-laqe8AMezMI/VJf31N1KURI/AAAAAAAAB3E/SuOKkukXWII/s1600/07.%E8%A8%AD%E5%AE%9A.png)</div>
設定中
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-R8j6Dj7YJTo/VJf35uPZ0SI/AAAAAAAAB3M/8ksf-XzMc4g/s1600/08.%E8%A8%AD%E5%AE%9A%E4%B8%AD.png)](http://1.bp.blogspot.com/-R8j6Dj7YJTo/VJf35uPZ0SI/AAAAAAAAB3M/8ksf-XzMc4g/s1600/08.%E8%A8%AD%E5%AE%9A%E4%B8%AD.png)</div>
設定成功
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-KhM64UpoxFs/VJf39DcDyZI/AAAAAAAAB3U/w2rrwM2efpo/s1600/09.%E8%A8%AD%E5%AE%9A%E6%88%90%E5%8A%9F.png)](http://2.bp.blogspot.com/-KhM64UpoxFs/VJf39DcDyZI/AAAAAAAAB3U/w2rrwM2efpo/s1600/09.%E8%A8%AD%E5%AE%9A%E6%88%90%E5%8A%9F.png)</div>
檢閱結果
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-PHlyy3_XnUo/VJf5A7FEELI/AAAAAAAAB3g/hO4_3N-v_5U/s1600/10.%E6%AA%A2%E9%96%B1%E7%B5%90%E6%9E%9C.png)](http://2.bp.blogspot.com/-PHlyy3_XnUo/VJf5A7FEELI/AAAAAAAAB3g/hO4_3N-v_5U/s1600/10.%E6%AA%A2%E9%96%B1%E7%B5%90%E6%9E%9C.png)</div>