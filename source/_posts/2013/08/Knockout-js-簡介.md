---
title: Knockout.js 簡介
tags:
  - Knockout
date: 2013-08-29 10:03:00
---

<div>Knockout.js是一套Javascript Library，主要用來處理網頁上MVVM模式的資料更新與繫結
要引用Knockout最方便的方式，不外就是透過Nuget </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-BdZy3etaPJw/Uh6rgtFjxBI/AAAAAAAAAys/WVfWTS9_ZtE/s1600/01.nuget.png)](http://1.bp.blogspot.com/-BdZy3etaPJw/Uh6rgtFjxBI/AAAAAAAAAys/WVfWTS9_ZtE/s1600/01.nuget.png)</div>
<div>Scripts資料夾中就會出現Knockout的檔案
knockout-{version}.js為壓縮版本
knockout-{version}.debug.js為末壓縮版本</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-8YCimjZDtUQ/Uh6rj1i1meI/AAAAAAAAAy0/BngICrtnWVI/s1600/02.scripts.png)](http://3.bp.blogspot.com/-8YCimjZDtUQ/Uh6rj1i1meI/AAAAAAAAAy0/BngICrtnWVI/s1600/02.scripts.png)</div><div>knockout的使用方式，首先宣告一個ViewModel類別，然後透過ko.applyBindings來繫結這個類別
除了顯示資料之外，也支援雙向繫結
以下是一個簡單的例子 </div>
<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="300" src="http://jsfiddle.net/vcMUH/embedded/" width="100%"></iframe></div>