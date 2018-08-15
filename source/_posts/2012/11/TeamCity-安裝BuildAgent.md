---
title: TeamCity 安裝BuildAgent
tags:
  - BuildAgent
  - TeamCity
date: 2012-11-29 22:46:00
---

<div class="separator" style="clear: both; text-align: left;">首先下載BuildAgent </div>
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-ljIYNJqcFMA/ULd0mqvusZI/AAAAAAAAAgU/rhd3IZP6gIA/s1600/01.Download.png)](http://1.bp.blogspot.com/-ljIYNJqcFMA/ULd0mqvusZI/AAAAAAAAAgU/rhd3IZP6gIA/s1600/01.Download.png)</div>
<div class="separator" style="clear: both; text-align: left;">把安裝程式傳送到目標電腦後，一直按下一步安裝就可以了</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Nl-fVttlNvY/ULd01UChNnI/AAAAAAAAAgc/uCdjsRJa3Q0/s1600/02.Install.png)](http://3.bp.blogspot.com/-Nl-fVttlNvY/ULd01UChNnI/AAAAAAAAAgc/uCdjsRJa3Q0/s1600/02.Install.png)</div>
<div class="separator" style="clear: both; text-align: left;">安裝好後，到BuildAgent下面的conf資料夾，找到buildAgent.properties設定檔</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-DlsAiWRF11g/ULd05S1cHrI/AAAAAAAAAgk/qyERkuG3M3A/s1600/03.Conf.png)](http://2.bp.blogspot.com/-DlsAiWRF11g/ULd05S1cHrI/AAAAAAAAAgk/qyERkuG3M3A/s1600/03.Conf.png)</div>
<div class="separator" style="clear: both; text-align: left;">確認一下ServerURL是否正確，要注意用反斜線來表示的跳脫字元</div>順利連線之後，約1~2分鐘，最下面就會出現authorizationToken
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-f_JZU5qJLdI/ULd0-Dch_OI/AAAAAAAAAgs/tH_uctbiWLU/s1600/04.UnAuthorized.png)](http://1.bp.blogspot.com/-f_JZU5qJLdI/ULd0-Dch_OI/AAAAAAAAAgs/tH_uctbiWLU/s1600/04.UnAuthorized.png)</div>
<div class="separator" style="clear: both; text-align: left;">登入TeamCity，也會看到未授權的記錄，把剛那組授權碼輸入就行了</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-ErLooHee9vA/ULd1CY7_XvI/AAAAAAAAAg0/ku4uJzh7nVQ/s1600/05.Authorized.png)](http://1.bp.blogspot.com/-ErLooHee9vA/ULd1CY7_XvI/AAAAAAAAAg0/ku4uJzh7nVQ/s1600/05.Authorized.png)</div>
<div class="separator" style="clear: both; text-align: left;">等待一陣子，Connected就會有剛安裝的BuildAgent了 </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-BpS-6DA0Di8/ULd1FrO0EzI/AAAAAAAAAg8/OSZQBP1KXDw/s1600/06.Connect.png)](http://1.bp.blogspot.com/-BpS-6DA0Di8/ULd1FrO0EzI/AAAAAAAAAg8/OSZQBP1KXDw/s1600/06.Connect.png)</div>
<div class="separator" style="clear: both; text-align: left;">上一篇:[TeamCity 改用網域帳號LDAP登入](http://blog.developer.idv.tw/2012/11/teamcity-ldap.html)</div>