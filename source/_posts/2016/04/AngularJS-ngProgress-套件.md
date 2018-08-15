---
title: AngularJS ngProgress 套件
tags:
  - AngularJS套件
date: 2016-04-08 17:39:00
---

# 安裝指令

    <span class="hljs-variable">$ </span>bower install ngprogress`</pre>

    # 加入css和js
    <pre class="prettyprint">`<span class="hljs-tag">&lt;<span class="hljs-title">script</span> <span class="hljs-attribute">src</span>=<span class="hljs-value">"app/components/ngProgress/ngProgress.min.js"</span>&gt;</span><span class="javascript"></span><span class="hljs-tag">&lt;/<span class="hljs-title">script</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-title">link</span> <span class="hljs-attribute">rel</span>=<span class="hljs-value">"stylesheet"</span> <span class="hljs-attribute">href</span>=<span class="hljs-value">"ngProgress.css"</span>&gt;</span>`</pre>

    # 載入模組
    <pre class="prettyprint">`<span class="hljs-keyword">var</span> app = angular.module(<span class="hljs-string">'progressApp'</span>, [<span class="hljs-string">'ngProgress'</span>]);`</pre>

    # 注入控制器
    <pre class="prettyprint">`<span class="hljs-keyword">var</span> MainCtrl = <span class="hljs-function"><span class="hljs-keyword">function</span><span class="hljs-params">($scope, $timeout, ngProgressFactory)</span> {</span>}`</pre>

    # 建立進度條物件
    <pre class="prettyprint">`$scope.progressbar = ngProgressFactory.createInstance();`</pre>

    # 啟動進度條
    <pre class="prettyprint">`$scope.progressbar.start();
    $timeout($scope.progressbar.complete(), <span class="hljs-number">1000</span>);`</pre>

    # API
    <pre class="prettyprint">`-<span class="ruby"> <span class="hljs-symbol">start:</span> 啟動進度條
    </span>-<span class="ruby"> <span class="hljs-symbol">setHeight:</span> 設定進度條高度
    </span>-<span class="ruby"> <span class="hljs-symbol">setColor:</span> 設定進度條顏色
    </span>-<span class="ruby"> <span class="hljs-symbol">status:</span> 進度條狀態
    </span>-<span class="ruby"> <span class="hljs-symbol">stop:</span> 停止進度條
    </span>-<span class="ruby"> <span class="hljs-symbol">set:</span> 設定進度
    </span>-<span class="ruby"> <span class="hljs-symbol">reset:</span> 重設進度
    </span>-<span class="ruby"> <span class="hljs-symbol">complete:</span> 完成進度
    </span>-<span class="ruby"> <span class="hljs-symbol">setParent:</span> 設定進度條上層原素
    </span>-<span class="ruby"> <span class="hljs-symbol">getDomElement:</span> 取得進度條元素</span>

# 相關連結
[ngProgress 官網](http://victorbjelkholm.github.io/ngProgress/#demo "ngProgress 官網")
[ngProgress GitHub](https://github.com/victorbjelkholm/ngprogress "ngProgress GitHub")