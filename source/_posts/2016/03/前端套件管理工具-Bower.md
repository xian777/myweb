---
title: '前端套件管理工具: Bower'
tags:
  - NodeJS
date: 2016-03-15 15:47:00
---

<div>安裝bower</div><div><pre class="brush:bash">$ npm install bower -g</pre></div>
<div>產生設定檔</div><div><pre class="brush:bash">$ bower init</pre></div><div>
<div><pre class="brush:javascript">{
  "name": "ASP.NET",
  "private": true,
  "dependencies": {
    "bootstrap": "3.3.5",
    "jquery": "2.1.4",
    "jquery-validation": "1.14.0",
    "jquery-validation-unobtrusive": "3.2.4",
    "angularjs": "1.5.0"
  }
}</pre></div><div>
新增.bowerrc檔案輸入資料夾位置</div><div><pre class="brush:javascript">{
  "directory": "wwwroot/lib"
}</pre></div>

<div>安裝套件</div><div><pre class="brush:bash">$ bower install
$ bower install jquery
$ bower install jquery --save
$ bower install jquery --save-dev</pre></div>

<div>查詢套件</div><div><pre class="brush:bash">$ bower search jquery</pre></div>

<div>查詢指定套件詳細訊息 </div><div><pre class="brush:bash">$ bower info jquery</pre></div>

<div>查詢已安裝套件</div><div><pre class="brush:bash">$ bower list</pre></div>

<div>移除套件</div><div><pre class="brush:bash">$ bower uninstall jquery</pre></div>

</div>