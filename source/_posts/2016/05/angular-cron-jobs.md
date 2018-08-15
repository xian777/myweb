---
title: angular-cron-jobs
tags:
  - AngularJS套件
date: 2016-05-23 17:07:00
---

# angular-cron-jobs
angular-cron-jobs是用來轉換crontab語法的介面

## 安裝
```shell
bower install angular-cron-jobs
```

## 載入模組
```javascript
angular.module('myApp', ['angular-cron-jobs']);
```

## 用法
* output:輸出值
* config:設定值
* init:初始值
```html
&lt;cron-selection output="myOutput" config="myConfig" init="serverData"&gt;&lt;/cron-selection&gt;
```

## 設定值
```javascript
$scope.myConfig = {
&nbsp; &nbsp; options: {
&nbsp; &nbsp; &nbsp; &nbsp; allowWeek : false,
&nbsp; &nbsp; &nbsp; &nbsp; allowMonth : false,
&nbsp; &nbsp; &nbsp; &nbsp; allowYear : false
&nbsp; &nbsp; }
}
```