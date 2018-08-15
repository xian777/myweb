---
title: Server2008R2 System佔用80Port的問題
tags:
  - 茶包射手
date: 2014-07-07 17:02:00
---

最近常碰到80Port被作業系統佔用的問題，原因大部份都是不正常關機引起來
每隔一段時間要找解法，總是忘了一些關鍵字，所以在此備忘一下

首先打開命令字元，透過netstat的-o選項，可以顯示出佔用的PID
小技巧是透過管線用findstr過濾80 port，資料會更清楚一些
netstat -nao | findstr 80
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-SSuCyUSsSnw/U7pgnq53qPI/AAAAAAAABho/hg6SklZ9agY/s1600/01.pid.png)](http://4.bp.blogspot.com/-SSuCyUSsSnw/U7pgnq53qPI/AAAAAAAABho/hg6SklZ9agY/s1600/01.pid.png)</div>
打開工作管理員，可以看到PID4是SYSTEM
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-9GhaTmuwWkI/U7phN98gW7I/AAAAAAAABhw/5m-VC4rZZAA/s1600/04.task.png)](http://2.bp.blogspot.com/-9GhaTmuwWkI/U7phN98gW7I/AAAAAAAABhw/5m-VC4rZZAA/s1600/04.task.png)</div>
先用net stop http關閉http服務
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-AIUUtYYITAY/U7phTeHe4tI/AAAAAAAABh4/A0yys6zFSa4/s1600/02.stop.png)](http://2.bp.blogspot.com/-AIUUtYYITAY/U7phTeHe4tI/AAAAAAAABh4/A0yys6zFSa4/s1600/02.stop.png)</div>

再用sc config http start= disabled就行了
<span style="color: red;">注意等號和值之間必須空一格</span>
然後重開機就解決囉
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-VNI45eKIgAw/U7phWLo6uEI/AAAAAAAABiA/2hAReHUC9mA/s1600/03.disabled.png)](http://4.bp.blogspot.com/-VNI45eKIgAw/U7phWLo6uEI/AAAAAAAABiA/2hAReHUC9mA/s1600/03.disabled.png)</div>