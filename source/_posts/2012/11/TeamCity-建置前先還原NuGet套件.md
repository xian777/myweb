---
title: TeamCity 建置前先還原NuGet套件
tags:
  - NuGet
  - TeamCity
date: 2012-11-13 22:13:00
---

## 當專案開始使用NuGet來管理套件時，預設套件會安裝在方案檔所在目錄的packages資料夾下
![](http://1.bp.blogspot.com/-Fb-XAssHj4w/UKJTn5RDetI/AAAAAAAAAbc/0mO3150CpWQ/s1600/01.Packages.png)](http://1.bp.blogspot.com/-Fb-XAssHj4w/UKJTn5RDetI/AAAAAAAAAbc/0mO3150CpWQ/s1600/01.Packages.png)

## 一般不會把這個套件這個資料夾加入原始檔控制以節省空間，而會在Vistual Studio中啟用套件還原
在方案檔上按右鍵就會看到這個選項了
![](http://1.bp.blogspot.com/-dyZVt873N58/UKJTobl3ClI/AAAAAAAAAbk/NhajJ3Li0bg/s1600/02.PackageRestore.png)](http://1.bp.blogspot.com/-dyZVt873N58/UKJTobl3ClI/AAAAAAAAAbk/NhajJ3Li0bg/s1600/02.PackageRestore.png)

## 按下後會有一個提示訊息，主要是會新增一個方案資料夾的提示
![](http://2.bp.blogspot.com/-6K_7ZRaH-U0/UKJTo96X_eI/AAAAAAAAAbs/F67Lyeec0TM/s1600/03.AlertMsg.png)](http://2.bp.blogspot.com/-6K_7ZRaH-U0/UKJTo96X_eI/AAAAAAAAAbs/F67Lyeec0TM/s1600/03.AlertMsg.png)

## 按下是(Y)之前，就會多出一個.nuget的方案資料夾
![](http://4.bp.blogspot.com/-y91qsRmScLI/UKJTpo9UQUI/AAAAAAAAAb0/6o_pDPgV6-A/s1600/04.NuGetDir.png)](http://4.bp.blogspot.com/-y91qsRmScLI/UKJTpo9UQUI/AAAAAAAAAb0/6o_pDPgV6-A/s1600/04.NuGetDir.png)

## 還要允許NuGet在建置期間下載遺漏的套件
![](http://1.bp.blogspot.com/-HcrmcbS0_2c/UKJTqBojMQI/AAAAAAAAAb8/twadrgujphw/s1600/05.AllowDownload.png)](http://1.bp.blogspot.com/-HcrmcbS0_2c/UKJTqBojMQI/AAAAAAAAAb8/twadrgujphw/s1600/05.AllowDownload.png)

## 把.nuget這個方案資料夾加入Source Control
![](http://4.bp.blogspot.com/-rGNsuEcMug8/UKJTqeyIARI/AAAAAAAAAcE/X_gwllNs14o/s1600/06.NuGetSVNDir.png)](http://4.bp.blogspot.com/-rGNsuEcMug8/UKJTqeyIARI/AAAAAAAAAcE/X_gwllNs14o/s1600/06.NuGetSVNDir.png)

## 先在TeamCity中安裝NuGet Command Line工具
![](http://2.bp.blogspot.com/-D5zrJvyfRKE/UKJTq18pInI/AAAAAAAAAcM/ikPaGWFbePw/s1600/07.AddNuGetExe.png)](http://2.bp.blogspot.com/-D5zrJvyfRKE/UKJTq18pInI/AAAAAAAAAcM/ikPaGWFbePw/s1600/07.AddNuGetExe.png)

## 新增一個Build Step，選擇NuGet Installer
選擇NuGet的版本，和輸入NuGet的來源
如果使用的套件是從NuGet官網來的，那直接保持空白
如果會使用其他來源的套件，就要在此輸入網址 
再輸入方案檔的相對路徑就行了
![](http://1.bp.blogspot.com/--zcz92kuTII/UKJTrZfOVWI/AAAAAAAAAcU/VjDyBdBpBLU/s1600/08.PreInstall.png)](http://1.bp.blogspot.com/--zcz92kuTII/UKJTrZfOVWI/AAAAAAAAAcU/VjDyBdBpBLU/s1600/08.PreInstall.png)

## 再來要把NuGet Install這個動作，放到編譯之前
所以按一下Reorder build steps，然後用拖曳的方式調整步驟後按Apply
![](http://2.bp.blogspot.com/-3BcMkxmRzyc/UKJTsEam9hI/AAAAAAAAAcc/Uj9RBGmTYP8/s1600/09.ReOrderStep.png)](http://2.bp.blogspot.com/-3BcMkxmRzyc/UKJTsEam9hI/AAAAAAAAAcc/Uj9RBGmTYP8/s1600/09.ReOrderStep.png)

## 再次建置就成功了
![](http://3.bp.blogspot.com/-hTTzcZcJpos/UKJTtmr7FLI/AAAAAAAAAck/MQKYRgqxUJ0/s1600/10.BuildSuccess.png)](http://3.bp.blogspot.com/-hTTzcZcJpos/UKJTtmr7FLI/AAAAAAAAAck/MQKYRgqxUJ0/s1600/10.BuildSuccess.png)