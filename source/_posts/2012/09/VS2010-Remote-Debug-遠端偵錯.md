---
title: VS2010 Remote Debug 遠端偵錯
tags:
  - Remote Debug
  - 遠端偵錯
date: 2012-09-28 15:09:00
---

## 前言
很多時後特別是設定檔的原因，直接在開發環境的伺服器上面遠端偵錯，比較容易找到問題點，但ASP.NET的遠端偵錯之前一直搞不定，後來爬了許多文並做了多次的試驗後才搞定，主要問題分成兩個部份，防火牆的設定相對來說比較簡單，大部份都是帳號權限的問題比較麻煩，在此記錄一下，以供日後老年癡呆的時後服用

## 首先先從簡單的防火牆設定開始 
[http://msdn.microsoft.com/zh-tw/library/ee126350%28v=vs.100%29.aspx](http://msdn.microsoft.com/zh-tw/library/ee126350%28v=vs.100%29.aspx)

* 本機防火牆設定
* 遠端偵錯 DCOM:TCP 135
* 遠端偵錯 DCOM UDP IPSec UDP:500,4500
* 允許Vistual Studio接收網路訊息
* SystemDrive:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\devenv.exe

## 在附加執行緒的時後，如果本機的防火牆設定沒開，預設就會跳出這個訊息 
[![](http://4.bp.blogspot.com/-RkY1C_Z9hx4/UGU9hlLUyHI/AAAAAAAAAEA/mMsKP-1gfnc/s1600/msg1.png)](http://4.bp.blogspot.com/-RkY1C_Z9hx4/UGU9hlLUyHI/AAAAAAAAAEA/mMsKP-1gfnc/s1600/msg1.png)


## 選擇解除了就會幫你打開相對應的Port 
[![](http://2.bp.blogspot.com/-9R6ifqiBrq0/UGU8yzpglxI/AAAAAAAAADw/kn03FHW8aKk/s1600/firewallStatus.png)](http://2.bp.blogspot.com/-9R6ifqiBrq0/UGU8yzpglxI/AAAAAAAAADw/kn03FHW8aKk/s1600/firewallStatus.png)
* 遠端防火牆設定
* 遠端偵錯 DCOM TCP 135
* IPSec 遠端偵錯 DCOM UDP 500, 4500
* 遠端偵錯檔案及印表機 TCP 139, 445
* 遠端偵錯檔案及印表機 UDP 137, 138
* 為 Visual Studio msvcmon.exe 處理序新增例外
* SystemDrive:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE

## 在伺服器上面使用遠端偵錯工具組態精靈進行設定比較簡單
[![](http://3.bp.blogspot.com/-wZ9f9Ucf-1M/UGU9RCFmc0I/AAAAAAAAAD4/rT6Fs1QMwc0/s1600/firewall.png)](http://3.bp.blogspot.com/-wZ9f9Ucf-1M/UGU9RCFmc0I/AAAAAAAAAD4/rT6Fs1QMwc0/s1600/firewall.png)

## 再來就是問題比較多的帳號權限問題
[http://msdn.microsoft.com/zh-tw/library/9y5b4b4f.aspx](http://msdn.microsoft.com/zh-tw/library/9y5b4b4f.aspx)

* 重點1:每台電腦上都必須有本機使用者帳戶，而且兩個帳戶的使用者名稱和密碼都必須相同
* 重點2:如果您要以不同的使用者帳戶執行

剛開始我是在本機和遠端都另外開一個帳號，密碼都一樣，在內部開發環境中順利執行遠端偵錯
但後來換了線上環境，卻又發生帳號權限問題，再多爬一些文後，才發現問題在這裡
也就是說本機附加執行緒的時後，用的是打開Visual Studio的帳號連線到遠端
而遠端接收連線後也要連回來本機，用的是打開msvsmon的帳號
開發環境隨便搞都沒關系，但線上環境就不能亂動了，更何況是加帳號
所以最簡單的方法，就是使用遠端的管理員帳號，然後讓本機來配合遠端的密碼，首先開啟遠端的偵錯工具

[![](http://3.bp.blogspot.com/-H14pjWnipTQ/UGVJ_ViNXmI/AAAAAAAAAEQ/4T26B06elIU/s1600/step1.png)](http://3.bp.blogspot.com/-H14pjWnipTQ/UGVJ_ViNXmI/AAAAAAAAAEQ/4T26B06elIU/s1600/step1.png)

## 接下來在本機，在Vistual Studio的連結上使用Shift + 右鍵，然後選擇以不同的身份者執行
[![](http://4.bp.blogspot.com/-2QxyK1q7644/UGVLoI2J1TI/AAAAAAAAAEY/IUDLZLvRWTY/s1600/step2.png)](http://4.bp.blogspot.com/-2QxyK1q7644/UGVLoI2J1TI/AAAAAAAAAEY/IUDLZLvRWTY/s1600/step2.png)

## 再來就是輸入本機的.\Administrator和密碼，當然密碼要改成和遠端的一樣，接下來就附加緒，在限定詞中輸入IP就可以了
[![](http://4.bp.blogspot.com/-DkoPcZevzJw/UGVLpBiPyPI/AAAAAAAAAEc/cU1_yv5fPtM/s1600/step3.png)](http://4.bp.blogspot.com/-DkoPcZevzJw/UGVLpBiPyPI/AAAAAAAAAEc/cU1_yv5fPtM/s1600/step3.png)