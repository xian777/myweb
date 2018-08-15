---
title: TeamCity 刪除特定的Nuget Package
tags:
  - TeamCity
  - 茶包射手
date: 2013-10-09 11:02:00
---

因為設定上的問題，從TeamCity所生成管理的Nuget package的版本號碼會有衝突
所以需要把有問題的package先刪除
但TeamCity本身沒有直接支援刪除的功能，找到了一篇用reset api刪除的方式

利用Filddler來執行rest api，網址為http://&lt;teamcity&gt;/httpAuth/app/rest/builds/id
最後的id為指定的建置版本，也是要刪除的版本
可以很容易的在一些設定頁面上，找一下網址後面的BuildId所帶的值來取得
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-xekiyDv1rtQ/UlTFBOBUZGI/AAAAAAAAA04/n4AzSukSpX0/s1600/buildid.png)](http://1.bp.blogspot.com/-xekiyDv1rtQ/UlTFBOBUZGI/AAAAAAAAA04/n4AzSukSpX0/s1600/buildid.png)</div>

使用Filddler執行DELETE方法，並在標頭中加入Authorization: Basic (UserName:Password)就行了
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-4_P16nZPh-U/UlTHONRcYWI/AAAAAAAAA1g/oSlRrBdtPac/s1600/teamcity.png)](http://4.bp.blogspot.com/-4_P16nZPh-U/UlTHONRcYWI/AAAAAAAAA1g/oSlRrBdtPac/s1600/teamcity.png)</div>

括號內的帳密需要用base64編碼，利用TextWizard來轉換就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Be-SvqI7AUY/UlTGMe3pauI/AAAAAAAAA1Q/mERbs8tNtOc/s1600/base64.png)](http://3.bp.blogspot.com/-Be-SvqI7AUY/UlTGMe3pauI/AAAAAAAAA1Q/mERbs8tNtOc/s1600/base64.png)</div>
<div class="separator" style="clear: both; text-align: center;"></div>
參考連結

[http://stackoverflow.com/questions/10218318/how-to-remove-a-specific-version-of-a-package-on-a-teamcity-nuget-feed](http://stackoverflow.com/questions/10218318/how-to-remove-a-specific-version-of-a-package-on-a-teamcity-nuget-feed)

[Fiddler 下載](http://fiddler2.com/)