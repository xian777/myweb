---
title: 架設Nuget.Server
tags:
  - NuGet
date: 2012-10-17 11:15:00
---

## 首先建立一個空白的Web應用程式專案
[![](http://3.bp.blogspot.com/-5RPTDkv_WAw/UH4fA3LkznI/AAAAAAAAAIM/KkYwIituHkA/s1600/01.NewProject.png)](http://3.bp.blogspot.com/-5RPTDkv_WAw/UH4fA3LkznI/AAAAAAAAAIM/KkYwIituHkA/s1600/01.NewProject.png)

## 再來使用Nuget安裝Nuget.Server這個套件
![](http://1.bp.blogspot.com/-Y35bQtZfSsY/UH4fBo6X46I/AAAAAAAAAIQ/Nw3tlc4gEtU/s1600/02.NugetServer.png)](http://1.bp.blogspot.com/-Y35bQtZfSsY/UH4fBo6X46I/AAAAAAAAAIQ/Nw3tlc4gEtU/s1600/02.NugetServer.png)

## VS2012需檢查一下是否有兩個compilation區段
![](http://3.bp.blogspot.com/-MBIm4bi6t0s/UH4fCb-AHtI/AAAAAAAAAIY/bZx8QYobEO8/s1600/03.ConfigError.png)](http://3.bp.blogspot.com/-MBIm4bi6t0s/UH4fCb-AHtI/AAAAAAAAAIY/bZx8QYobEO8/s1600/03.ConfigError.png)

## 順便設定一下apiKey，這是之後用來上傳package的密碼
![](http://3.bp.blogspot.com/-nf5rin61TbM/UH4fDWK1JaI/AAAAAAAAAIk/46OQrDyq65A/s1600/04.ApiKey.png)](http://3.bp.blogspot.com/-nf5rin61TbM/UH4fDWK1JaI/AAAAAAAAAIk/46OQrDyq65A/s1600/04.ApiKey.png)

* 設定完後，按下F5應該會看到這樣的畫面
* 上面的網址是查詢Nuget套件資訊用的
* 下面的命令是之後用command line工具上傳套件的指令格式
![](http://1.bp.blogspot.com/-1rhRqaKxNi4/UH4fESz8e6I/AAAAAAAAAIo/KBPtNfg9k5w/s1600/05.Default.png)](http://1.bp.blogspot.com/-1rhRqaKxNi4/UH4fESz8e6I/AAAAAAAAAIo/KBPtNfg9k5w/s1600/05.Default.png)

* 工具-&gt;選項-&gt;套件管理員-&gt;套件來源
* 在這裡把剛的網址設定上去
![](http://1.bp.blogspot.com/-PAeK1lQ1tpY/UH4fEysT_-I/AAAAAAAAAIw/-9rtYt4W5T8/s1600/06.Setting.png)](http://1.bp.blogspot.com/-PAeK1lQ1tpY/UH4fEysT_-I/AAAAAAAAAIw/-9rtYt4W5T8/s1600/06.Setting.png)

## 使用Nuget的時後，就會發現多了一個來源
![](http://3.bp.blogspot.com/-fZlBCZsU2i8/UH4ifzL3qtI/AAAAAAAAAJI/D1EF7scCW9Y/s1600/07.source.png)](http://3.bp.blogspot.com/-fZlBCZsU2i8/UH4ifzL3qtI/AAAAAAAAAJI/D1EF7scCW9Y/s1600/07.source.png)