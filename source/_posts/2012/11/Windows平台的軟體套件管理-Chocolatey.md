---
title: 'Windows平台的軟體套件管理:Chocolatey'
tags: []
date: 2012-11-06 13:56:00
---

先到[官網](http://chocolatey.org/)逛一下，安裝的方式很簡單，打開一個cmd，切到C:\，直接在官網上的那一串複製貼上就好了

```shell
C:\@powershell -NoProfile -ExecutionPolicy unrestricted  -Command "iex ((new-object  net.webclient .DownloadString('http://bit.ly/psChocInstall'))"  &amp;&amp; SET PATH=%PATH%;%systemdrive%\chocolatey\bin
```

如果有Vistual Studio，也安裝Nuget套件的話，也可以用命令列安裝chocolatey套件`
Install-Package chocolatey`

如果有nuget命令列工具的話，直接安裝也可以`
nuget install chocolatey`

安裝好之後，可在官網搜尋目前有的套件，常見的像``tortoisesvn、Radmin.Viewer、7zip，只要執行cinst 套件名稱就可以安裝了，還滿方便的