---
title: svn migration to git
tags:
  - git
date: 2016-09-30 09:12:00
---

首先下載subgit，需要先安裝好JAVA環境
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-WHgp_trAbNo/V-26bWM_UjI/AAAAAAAAEIk/EYrM4H_RPPAHpMDLqQlsYc_HB44XmVghgCLcB/s1600/01.png)](https://3.bp.blogspot.com/-WHgp_trAbNo/V-26bWM_UjI/AAAAAAAAEIk/EYrM4H_RPPAHpMDLqQlsYc_HB44XmVghgCLcB/s1600/01.png)</div>

解壓縮後開啟命令列工具到bin資料夾，輸入指令
subgit import --non-interactive --default-domain example.com --svn-url https://svnurl/svn/ExampleProjectName ExampleProjectName
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-64W4fqUASBs/V-26bj589cI/AAAAAAAAEIs/iz9lOQ6-c_46nLtpFPHJYZIxpWJujxWIACLcB/s1600/02.png)](https://1.bp.blogspot.com/-64W4fqUASBs/V-26bj589cI/AAAAAAAAEIs/iz9lOQ6-c_46nLtpFPHJYZIxpWJujxWIACLcB/s1600/02.png)</div>

匯出成功後，再推送到git server
git push --mirror https://giturl/ExampleProjectName.git
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-U4IxN5KqWkE/V-26briOl8I/AAAAAAAAEIo/CJ2qjT_Tx7Qsi3Gz9hpXOsfMEAPuCnXUgCLcB/s1600/03.png)](https://4.bp.blogspot.com/-U4IxN5KqWkE/V-26briOl8I/AAAAAAAAEIo/CJ2qjT_Tx7Qsi3Gz9hpXOsfMEAPuCnXUgCLcB/s1600/03.png)</div>

這樣就轉移成功囉
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-CwDVvOuB2mI/V-26cDNV6FI/AAAAAAAAEIw/GHX1Udg6XVU2QCuEjCxbxMGqLubK7FozACLcB/s1600/04.png)](https://3.bp.blogspot.com/-CwDVvOuB2mI/V-26cDNV6FI/AAAAAAAAEIw/GHX1Udg6XVU2QCuEjCxbxMGqLubK7FozACLcB/s1600/04.png)</div>