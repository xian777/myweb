---
title: NuGet 套件超過30MB的問題
tags:
  - NuGet
date: 2012-11-06 13:28:00
---

## 前台
開始打包Web套件之後，套件的檔案很快就超過了30MB，使用NuGet Push的時後，一直顯示404找不到網頁，再到IIS查Log，回應碼是404.13，再Google一下，原來IIS7預設的上傳是30MB， 所以把這個值設大一點就好了，例如加大到300MB
```xml
<system.web>
       <httpRuntime maxRequestLength=”31457280” />
</system.web>
```

## 參考資料
* [30MB Default Maximum Nuget Package Size ](http://help.octopusdeploy.com/discussions/problems/184-30mb-default-maximum-nuget-package-size)
* [404.13 Not Found – Uploading Large Files with Integrated Pipeline!&nbsp;](http://martinondotnet.blogspot.tw/2010/04/iis-7-gotcha-40413-not-found-uploading.html)