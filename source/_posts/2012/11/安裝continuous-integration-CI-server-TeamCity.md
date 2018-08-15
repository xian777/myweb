---
title: '安裝continuous integration (CI) server:TeamCity'
tags:
  - Build Server
  - TeamCity
date: 2012-11-07 19:59:00
---

## 首先到[TeamCity的官網](http://www.jetbrains.com/teamcity/download/index.html)下載合適平台的安裝檔，這裡以Windows平台為例
![](http://2.bp.blogspot.com/-AXLFKiOYCwo/UJpLk6nWQEI/AAAAAAAAAUI/Pq6nhLyFBmo/s1600/01.Download.png)](http://2.bp.blogspot.com/-AXLFKiOYCwo/UJpLk6nWQEI/AAAAAAAAAUI/Pq6nhLyFBmo/s1600/01.Download.png)

## 接下來一直按下一步就行了
![](http://4.bp.blogspot.com/-bIHMy3RoffA/UJpLlYIgjwI/AAAAAAAAAUQ/qYC73ihpSTc/s1600/02.Install.png)](http://4.bp.blogspot.com/-bIHMy3RoffA/UJpLlYIgjwI/AAAAAAAAAUQ/qYC73ihpSTc/s1600/02.Install.png)

## 安裝的路徑
![](http://4.bp.blogspot.com/--R9vNZrd0c4/UJpQ16_40uI/AAAAAAAAAWY/Od-LiFqEP-U/s1600/03.InstallPath.png)](http://4.bp.blogspot.com/--R9vNZrd0c4/UJpQ16_40uI/AAAAAAAAAWY/Od-LiFqEP-U/s1600/03.InstallPath.png)

## 安裝的項目，可單獨選擇Build Agent或Server
![](http://3.bp.blogspot.com/-PXWB1fViYNo/UJpPYyre8vI/AAAAAAAAAWI/YJJCEISpev8/s1600/04.InstallItem.png)](http://3.bp.blogspot.com/-PXWB1fViYNo/UJpPYyre8vI/AAAAAAAAAWI/YJJCEISpev8/s1600/04.InstallItem.png)

## 設定檔的路徑
![](http://1.bp.blogspot.com/-xclD7A4hI5s/UJpPZahympI/AAAAAAAAAWQ/CVvhaGMYtts/s1600/05.AppPath.png)](http://1.bp.blogspot.com/-xclD7A4hI5s/UJpPZahympI/AAAAAAAAAWQ/CVvhaGMYtts/s1600/05.AppPath.png)

## 如果安裝的機器上面已經有Web伺服器的話，預設的Port就會改用8080
![](http://1.bp.blogspot.com/-hGBViNi4gSA/UJpLmB-UDII/AAAAAAAAAUY/0isL_frK7Uw/s1600/03.Port.png)](http://1.bp.blogspot.com/-hGBViNi4gSA/UJpLmB-UDII/AAAAAAAAAUY/0isL_frK7Uw/s1600/03.Port.png)

## 設定BuildAgent的環境，基本上會自動偵測，記住網域，按下Save就行了
![](http://2.bp.blogspot.com/-whsaUg0yWpY/UJpRYUAHXfI/AAAAAAAAAWg/Vu7tsT0mzSk/s1600/07.Config.png)](http://2.bp.blogspot.com/-whsaUg0yWpY/UJpRYUAHXfI/AAAAAAAAAWg/Vu7tsT0mzSk/s1600/07.Config.png)

## 選擇TeamCity Server Service要用的帳號
![](http://3.bp.blogspot.com/-zjQfaovl5qs/UJpLnMGHDNI/AAAAAAAAAUo/irM35PeE5fs/s1600/05.Account.png)](http://3.bp.blogspot.com/-zjQfaovl5qs/UJpLnMGHDNI/AAAAAAAAAUo/irM35PeE5fs/s1600/05.Account.png)

## 選擇TeamCity Agent Service要用的帳號
![](http://3.bp.blogspot.com/-oNK5Kj7vcuY/UJpLn2N21UI/AAAAAAAAAUw/HEisyuMEwII/s1600/06.AgentAccount.png)](http://3.bp.blogspot.com/-oNK5Kj7vcuY/UJpLn2N21UI/AAAAAAAAAUw/HEisyuMEwII/s1600/06.AgentAccount.png)

## 啟動服務
![](http://1.bp.blogspot.com/-jepVzX5K58E/UJpLojQtS0I/AAAAAAAAAU4/U9C7b4ee1co/s1600/07.StartService.png)](http://1.bp.blogspot.com/-jepVzX5K58E/UJpLojQtS0I/AAAAAAAAAU4/U9C7b4ee1co/s1600/07.StartService.png)

## 到此安裝完成，按下Finish開始設定頁面
![](http://1.bp.blogspot.com/-HtFXZHUHMQ8/UJpLpZd5AvI/AAAAAAAAAVA/G6P77ikRea0/s1600/08.ConfigOK.png)](http://1.bp.blogspot.com/-HtFXZHUHMQ8/UJpLpZd5AvI/AAAAAAAAAVA/G6P77ikRea0/s1600/08.ConfigOK.png)

## 第一次執行時的頁面，按下Proceed按鈕執行初始化動作
![](http://4.bp.blogspot.com/-g3yN6FR9TjE/UJpLp9Ow6RI/AAAAAAAAAVI/RBxGhby_zSE/s1600/09.FirstStart.png)](http://4.bp.blogspot.com/-g3yN6FR9TjE/UJpLp9Ow6RI/AAAAAAAAAVI/RBxGhby_zSE/s1600/09.FirstStart.png)

## 等待初始化完成後，會跳出使用者授權頁面
![](http://2.bp.blogspot.com/-L5ByFtFy_Y4/UJpLquKDRfI/AAAAAAAAAVQ/5DI2jjLBMy4/s1600/10.Authority.png)](http://2.bp.blogspot.com/-L5ByFtFy_Y4/UJpLquKDRfI/AAAAAAAAAVQ/5DI2jjLBMy4/s1600/10.Authority.png)

## 輸入一組管理用的帳號
![](http://3.bp.blogspot.com/-Ayhsa_UAN48/UJpLrb1JDoI/AAAAAAAAAVY/Nl-NBuv3UlY/s1600/11.AdminAccount.png)](http://3.bp.blogspot.com/-Ayhsa_UAN48/UJpLrb1JDoI/AAAAAAAAAVY/Nl-NBuv3UlY/s1600/11.AdminAccount.png)

## 登入成功，接下來就可以開始來設定專案了
![](http://3.bp.blogspot.com/-MkG9bg7OfcM/UJpLrzh3SDI/AAAAAAAAAVg/XVqnth93x3s/s1600/12.InstallOK.png)](http://3.bp.blogspot.com/-MkG9bg7OfcM/UJpLrzh3SDI/AAAAAAAAAVg/XVqnth93x3s/s1600/12.InstallOK.png)

## 參考資料
* [TeamCity Edition Comparison Matrix](http://www.jetbrains.com/teamcity/buy/edition_comparison.html)