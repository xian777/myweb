---
title: TeamCity 安裝 Octopus Deploy Integration 套件
tags:
  - Octopus
  - TeamCity
date: 2014-09-29 14:46:00
---

首先到官網下載TeamCity Plugin
[http://octopusdeploy.com/downloads](http://octopusdeploy.com/downloads)

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-XNxjbgrc77Q/VCj_gC3rSjI/AAAAAAAABms/w1bLqfUxOcs/s1600/01.%E5%AE%98%E7%B6%B2%E4%B8%8B%E8%BC%89.png)](http://3.bp.blogspot.com/-XNxjbgrc77Q/VCj_gC3rSjI/AAAAAAAABms/w1bLqfUxOcs/s1600/01.%E5%AE%98%E7%B6%B2%E4%B8%8B%E8%BC%89.png)</div>

把下載的zip檔，丟到TeamCity的Plugins資料夾下面
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-xoW5bvFoc8w/VCj_keKfYlI/AAAAAAAABm0/gMG9MFtcUbU/s1600/03.Plugins%E8%B3%87%E6%96%99%E5%A4%BE.png)](http://4.bp.blogspot.com/-xoW5bvFoc8w/VCj_keKfYlI/AAAAAAAABm0/gMG9MFtcUbU/s1600/03.Plugins%E8%B3%87%E6%96%99%E5%A4%BE.png)</div>

重新啟動TeamCity後，就可以在Plugin列表中看到Octopus Deploy Integration套件
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-c9eevtd_CIA/VCj_tFiOC2I/AAAAAAAABm8/Hqca2hI8jyk/s1600/04.Plugin%E5%88%97%E8%A1%A8.png)](http://3.bp.blogspot.com/-c9eevtd_CIA/VCj_tFiOC2I/AAAAAAAABm8/Hqca2hI8jyk/s1600/04.Plugin%E5%88%97%E8%A1%A8.png)</div>

在TeamCity的建置步驟中，會多出三個Runner
Create release是新增發行版本，也可以順便部署的指定的環境
Deploy release是部署指定版本
Promote是把現有的版本從指定的環境部署到其他環境
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-8sf6WLcQtJ0/VCkBHJGU0rI/AAAAAAAABnE/j8I-2xap158/s1600/06.TeamCity%E5%BB%BA%E7%BD%AE%E6%96%B0%E5%A2%9E%E9%A0%85%E7%9B%AE.png)](http://4.bp.blogspot.com/-8sf6WLcQtJ0/VCkBHJGU0rI/AAAAAAAABnE/j8I-2xap158/s1600/06.TeamCity%E5%BB%BA%E7%BD%AE%E6%96%B0%E5%A2%9E%E9%A0%85%E7%9B%AE.png)</div>

在VS建置Runner中，也會多出一個OctoPack的設定項目
勾選後會在建置參數中加入/p:RunOctoPack=true
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ugwpKzT9x9Y/VCkBRaltmnI/AAAAAAAABnM/1uDWOhBxUKE/s1600/05.VS%E6%96%B0%E5%A2%9E%E9%A0%85%E7%9B%AE.png)](http://2.bp.blogspot.com/-ugwpKzT9x9Y/VCkBRaltmnI/AAAAAAAABnM/1uDWOhBxUKE/s1600/05.VS%E6%96%B0%E5%A2%9E%E9%A0%85%E7%9B%AE.png)</div>

參考資料
官網的說明和影片
[http://docs.octopusdeploy.com/display/OD/TeamCity](http://docs.octopusdeploy.com/display/OD/TeamCity)