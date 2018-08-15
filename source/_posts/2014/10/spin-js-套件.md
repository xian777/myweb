---
title: spin.js 套件
tags:
  - NuGet套件
  - spin.js
date: 2014-10-01 14:05:00
---

spin.js是一個簡單使用的Loading的動畫，[官網](http://fgnass.github.io/spin.js/)上有很清楚的使用範例
首先透過NuGet安裝spin.js套件
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-frBwZAmeVK8/VCuYw17LqtI/AAAAAAAABs0/fWYi4xH2j6M/s1600/01.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)](http://1.bp.blogspot.com/-frBwZAmeVK8/VCuYw17LqtI/AAAAAAAABs0/fWYi4xH2j6M/s1600/01.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)</div>
網頁中放一個div來轉圈圈，再用一個按鈕來觸發事件
<div><pre class="brush:html">&lt;div id="div1"&gt;&lt;/div&gt;
&lt;input id="btn1" type="button" value="click" /&gt;
</pre></div>
spin.js本身是無相依性的，這邊用JQuery只是用來綁定事件
呼叫Spinner物件的spin函式來啟用動畫，呼叫stop來停止動畫
<div><pre class="brush:javascript">$(function () {
    $("#btn1").click(function () {
        spinner = new Spinner().spin($("#div1")[0]);
        setTimeout(function () {
            spinner.stop();
        }, 1000);
    });
});
</pre></div>

<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="300" src="http://jsfiddle.net/as0419gq/embedded/result,html,js" width="100%"></iframe></div>

相關資料
[Bootstrap button loading text](http://blog.developer.idv.tw/2014/10/bootstrap-button-loading-text.html)
[http://blog.developer.idv.tw/2014/10/bootstrap-button-loading-text.html](http://blog.developer.idv.tw/2014/10/bootstrap-button-loading-text.html)

[ladda-bootstrap 套件](http://blog.developer.idv.tw/2014/10/ladda-bootstrap.html)
[http://blog.developer.idv.tw/2014/10/ladda-bootstrap.html](http://blog.developer.idv.tw/2014/10/ladda-bootstrap.html)