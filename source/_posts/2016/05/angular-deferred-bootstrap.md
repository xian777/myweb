---
title: angular-deferred-bootstrap
tags:
  - AngularJS套件
date: 2016-05-23 18:03:00
---

# angular-deferred-bootstrap
angular-deferred-bootstrap是用來初始化angular應用程式的套件

# 安裝
```shell
bower install --save angular-deferred-bootstrap
```

# 用法
```javascript
deferredBootstrapper.bootstrap({
&nbsp; element: document.body,
&nbsp; module: 'MyApp',
&nbsp; resolve: {
&nbsp; &nbsp; APP_CONFIG: ['$http', function ($http) {
&nbsp; &nbsp; &nbsp; return $http.get('/api/demo-config');
&nbsp; &nbsp; }]
&nbsp; }
});
```

# 載入狀態css類別

* deferred-bootstrap-loading while the data is loading
* deferred-bootstrap-error if an error occurs in a resolve function and the app can not be bootstrapped

```css
#loading {
&nbsp; &nbsp; display: none;
}
.deferred-bootstrap-loading #loading {
&nbsp; &nbsp; display: block !important;
}

#error {
&nbsp; &nbsp; display: none;
}

.deferred-bootstrap-error #error {
&nbsp; &nbsp; display: block !important;
}

.loading-message{
&nbsp; &nbsp; text-align:center;
&nbsp; &nbsp; font-size:16pt;
}
```

# 載入狀態html
```html

&lt;div id="loading" class="side-body padding-top"&gt;
&nbsp; &nbsp; &lt;div class="progress progress-striped active"&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;div class="progress-bar" style="width: 100%;"&gt;&lt;/div&gt;
&nbsp; &nbsp; &lt;/div&gt;
&nbsp; &nbsp; &lt;p class="loading-message"&gt;Loading, please wait...&lt;/p&gt;
&lt;/div&gt;

&lt;div id="error" class="side-body padding-top"&gt;
&nbsp; &nbsp; &lt;div class="progress"&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;div class="progress-bar" style="width: 100%;"&gt;&lt;/div&gt;
&nbsp; &nbsp; &lt;/div&gt;
&nbsp; &nbsp; &lt;p class="loading-message"&gt;Loading fail, please try again...&lt;/p&gt;
&lt;/div&gt;
```