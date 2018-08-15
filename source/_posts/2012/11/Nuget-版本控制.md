---
title: Nuget 版本控制
tags:
  - NuGet
date: 2012-11-05 18:29:00
---

## 前台
NuGet正式套件的檔名，通常是這樣的格式:[id].[Major].[Minor].[Patch].nupkg
ex: MyPackage.1.0.1.nupkg
測試套件的檔名，通常格式為:id.[Major].[Minor].[Patch]-[alpha | beta | rc].nupkg

ex:
MyPackage.1.0.1-alpha.nupkg
MyPackage.1.0.1-beta.nupkg
MyPackage.1.0.1-rc.nupkg

* 有相依性的套件，指定的版號格式如下
* 直接指定版號為最低版號
* 小括號為不包含
* 中括號為包含
* 空白表示最新版號
1.0  = 1.0 ≤ x
(,1.0]  = x ≤ 1.0
(,1.0)  = x &lt; 1.0
[1.0] = x == 1.0
(1.0) = invalid
(1.0,) = 1.0 &lt; x
(1.0,2.0) = 1.0 &lt; x &lt; 2.0
[1.0,2.0] = 1.0 ≤ x ≤ 2.0
empty = latest version.

## 參考資料
* [Versioning](http://docs.nuget.org/docs/reference/versioning)