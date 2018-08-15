---
title: 架設SymbolSource.Server
tags:
  - NuGet
  - pdb
  - Symbol
date: 2012-10-21 17:19:00
---

## 首先要先安裝[Debugging Tools for Windows](http://msdn.microsoft.com/en-us/windows/hardware/gg463009)
![](http://1.bp.blogspot.com/-KzKeCG8zNjk/UIO4-cYGgII/AAAAAAAAAKU/wGhW5z4HeaQ/s1600/00.download.png)](http://1.bp.blogspot.com/-KzKeCG8zNjk/UIO4-cYGgII/AAAAAAAAAKU/wGhW5z4HeaQ/s1600/00.download.png)

## 記住這個安裝路徑，等下會用到
![](http://3.bp.blogspot.com/-QKH8P_Fpovo/UIO4J4JlA_I/AAAAAAAAAJk/5Yxs5DDK09I/s1600/00.Path.png)](http://3.bp.blogspot.com/-QKH8P_Fpovo/UIO4J4JlA_I/AAAAAAAAAJk/5Yxs5DDK09I/s1600/00.Path.png)

## 選擇安裝Debugging Tool for Windows，一直按下一步就好了
![](http://4.bp.blogspot.com/-eQQb6sjiNqE/UIO4JNm7ZzI/AAAAAAAAAJc/ClovhmG2kzU/s1600/00.DebuggingTool.png)](http://4.bp.blogspot.com/-eQQb6sjiNqE/UIO4JNm7ZzI/AAAAAAAAAJc/ClovhmG2kzU/s1600/00.DebuggingTool.png)

## 接下來開始安裝SymbolSource.Server
## 先開一個MVC專案
![](http://3.bp.blogspot.com/-weYfPMU9dLY/UIO4Koyl5eI/AAAAAAAAAJs/6Jp_tUUv1eQ/s1600/01.NewProject.png)](http://3.bp.blogspot.com/-weYfPMU9dLY/UIO4Koyl5eI/AAAAAAAAAJs/6Jp_tUUv1eQ/s1600/01.NewProject.png)

## 選擇空白範本
![](http://2.bp.blogspot.com/-2fqKnGX6JNA/UIO4LMBQMSI/AAAAAAAAAJ0/sBdNebIBvDo/s1600/02.ProjectSetting.png)](http://2.bp.blogspot.com/-2fqKnGX6JNA/UIO4LMBQMSI/AAAAAAAAAJ0/sBdNebIBvDo/s1600/02.ProjectSetting.png)

## 用Nuget安裝SymbolSource.Server.Basic套件
![](http://2.bp.blogspot.com/-vAS8yuexXc4/UIO4Lr-AvLI/AAAAAAAAAJ8/AqZbH0BG-mg/s1600/03.SymbolSourceServer.png)](http://2.bp.blogspot.com/-vAS8yuexXc4/UIO4Lr-AvLI/AAAAAAAAAJ8/AqZbH0BG-mg/s1600/03.SymbolSourceServer.png)

## 打開web.config，找到SrcSrvPath，修改成剛安裝的路徑
```xml
<add key="SrcSrvPath" value="C:\Program Files (x86)\Windows Kits\8.0\Debuggers\x64\srcsrv" />
```

## 按F5執行，就會看到如下的畫面
## 一個是Symbol的位置，一個是套件發佈用的位置
![](http://1.bp.blogspot.com/-3aEpzPPQ66g/UIO4MDpaxbI/AAAAAAAAAKE/qXzukxnN2mU/s1600/04.DefaultPage.png)](http://1.bp.blogspot.com/-3aEpzPPQ66g/UIO4MDpaxbI/AAAAAAAAAKE/qXzukxnN2mU/s1600/04.DefaultPage.png)

## 設定一下偵錯選項
1. 取消「啟用Just My Code的勾勾」
2. 勾選「啟用來源伺服器支援」
把套件和Symbol發佈之後就可以偵錯了
![](http://2.bp.blogspot.com/-dypoFu3nhYk/UIO4Ms8TdjI/AAAAAAAAAKM/eC0J2y1De5Q/s1600/05.Setting.png)](http://2.bp.blogspot.com/-dypoFu3nhYk/UIO4Ms8TdjI/AAAAAAAAAKM/eC0J2y1De5Q/s1600/05.Setting.png)

## 再新增一個Symbol位置，指向到伺服器路徑，之後發佈套件和Symbol就可以偵錯了
![](http://4.bp.blogspot.com/-7qcGV2EU9d8/UIO9MgH6h1I/AAAAAAAAAKs/huq9yb8Emso/s1600/06.Symbol.png)](http://4.bp.blogspot.com/-7qcGV2EU9d8/UIO9MgH6h1I/AAAAAAAAAKs/huq9yb8Emso/s1600/06.Symbol.png)

## 參考資料
* [Setting it up your own symbol and source server](http://www.symbolsource.org/Public/Blog/View/2012-03-13/Releasing_the_community_edition_of_SymbolSource)
* [Setting up your own SymbolSource Server: step-by-step ](http://blogs.realdolmen.com/experts/2012/08/07/setting-up-your-own-symbolsource-server-step-by-step/)