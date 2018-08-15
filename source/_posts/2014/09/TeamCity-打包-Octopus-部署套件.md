---
title: TeamCity 打包 Octopus 部署套件
tags:
  - Octopus
  - TeamCity
date: 2014-09-29 16:48:00
---

首先新建一個建置設定
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-1hnowCI7ZBM/VCkcK6DJ23I/AAAAAAAABpM/tcbGZTMFF7I/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://4.bp.blogspot.com/-1hnowCI7ZBM/VCkcK6DJ23I/AAAAAAAABpM/tcbGZTMFF7I/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>

設定SVN路徑
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-MbNEf3JsBJo/VCkcPahMcqI/AAAAAAAABpU/zj_3Q7qtu74/s1600/02.%E8%A8%AD%E5%AE%9Asvn.png)](http://4.bp.blogspot.com/-MbNEf3JsBJo/VCkcPahMcqI/AAAAAAAABpU/zj_3Q7qtu74/s1600/02.%E8%A8%AD%E5%AE%9Asvn.png)</div>

SVN的細部設定
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-j2ZooaYc4jU/VCkcXM4-fRI/AAAAAAAABpc/y22W60orsug/s1600/04.%E7%B4%B0%E9%83%A8%E8%A8%AD%E5%AE%9A.png)](http://4.bp.blogspot.com/-j2ZooaYc4jU/VCkcXM4-fRI/AAAAAAAABpc/y22W60orsug/s1600/04.%E7%B4%B0%E9%83%A8%E8%A8%AD%E5%AE%9A.png)</div>

取用trunk為根目錄
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-SNggN_J2dx4/VCkcbDRKANI/AAAAAAAABpk/CnjPPxJyhcs/s1600/03.%E6%8C%87%E5%AE%9Atrunk.png)](http://1.bp.blogspot.com/-SNggN_J2dx4/VCkcbDRKANI/AAAAAAAABpk/CnjPPxJyhcs/s1600/03.%E6%8C%87%E5%AE%9Atrunk.png)</div>
設定版號
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-58uT3yqTydA/VCkcfSDV4JI/AAAAAAAABps/BATMEcHU7zM/s1600/07.%E7%89%88%E8%99%9F.png)](http://4.bp.blogspot.com/-58uT3yqTydA/VCkcfSDV4JI/AAAAAAAABps/BATMEcHU7zM/s1600/07.%E7%89%88%E8%99%9F.png)</div>
第一個建置步驟是NuGet Installer，選擇方案檔即可
如果有自訂的NuGet來源，要記得輸入
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ysXS6Jmxytc/VCkckW2udOI/AAAAAAAABp0/xOI5ZJgOsjM/s1600/05.%E5%A5%97%E4%BB%B6%E9%82%84%E5%8E%9F.png)](http://2.bp.blogspot.com/-ysXS6Jmxytc/VCkckW2udOI/AAAAAAAABp0/xOI5ZJgOsjM/s1600/05.%E5%A5%97%E4%BB%B6%E9%82%84%E5%8E%9F.png)</div>

接下來可以建置專案了，勾選方案檔即可
在Run OctoPack這邊也勾選起來，輸入建置版號即可
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-umKldtIhOao/VCkcpdq-FAI/AAAAAAAABp8/k7DVLFr6_Yo/s1600/06.VS%E5%BB%BA%E7%BD%AE.png)](http://2.bp.blogspot.com/-umKldtIhOao/VCkcpdq-FAI/AAAAAAAABp8/k7DVLFr6_Yo/s1600/06.VS%E5%BB%BA%E7%BD%AE.png)</div>
建置成功就會得到打包好的套件
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-nz0WK09gIac/VCkcuMFYPtI/AAAAAAAABqE/Sg17Ph4-jqs/s1600/08.%E5%BB%BA%E7%BD%AE%E6%88%90%E5%8A%9F.png)](http://2.bp.blogspot.com/-nz0WK09gIac/VCkcuMFYPtI/AAAAAAAABqE/Sg17Ph4-jqs/s1600/08.%E5%BB%BA%E7%BD%AE%E6%88%90%E5%8A%9F.png)</div><div>
</div>