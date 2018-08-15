---
title: ladda-bootstrap 套件
tags:
  - NuGet套件
  - spin
date: 2014-10-01 14:33:00
---

ladda-bootstrap用將spin.js整合bootstrap，並加強功能的一個套件
[官網](http://msurguy.github.io/ladda-bootstrap/)上有很詳細的使用範例
透過NuGet就可以安裝
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-IughOK48vhE/VCuejPlOPuI/AAAAAAAABtE/x5bf4Vtf7PY/s1600/01.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)](http://1.bp.blogspot.com/-IughOK48vhE/VCuejPlOPuI/AAAAAAAABtE/x5bf4Vtf7PY/s1600/01.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)</div>
可以看到套件相依於spin.js
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-UqPTwSVmbmM/VCuenBELR-I/AAAAAAAABtM/iBFBfK9RyUo/s1600/02.%E5%A5%97%E4%BB%B6%E7%9B%B8%E4%BE%9D%E6%80%A7.png)](http://2.bp.blogspot.com/-UqPTwSVmbmM/VCuenBELR-I/AAAAAAAABtM/iBFBfK9RyUo/s1600/02.%E5%A5%97%E4%BB%B6%E7%9B%B8%E4%BE%9D%E6%80%A7.png)</div>

使用方式是在button上，加上ladda-button的css類別，要顯示的文字加上ladda-label的css類別
<div><pre class="brush:html">&lt;button id="btn1" class="btn btn-primary ladda-button" data-style="expand-left"&gt;
    &lt;span class="ladda-label"&gt;button&lt;/span&gt;
&lt;/button&gt;
</pre></div>
另外透過data-style來指定動畫效果
data-style="expand-left"
data-style="expand-right"
data-style="expand-up"
data-style="expand-down"
data-style="zoom-in"
data-style="zoom-out"
data-style="slide-left"
data-style="slide-right"
data-style="slide-up"
data-style="slide-down"
data-style="contract"

最後透過JavaScript來觸發，先用Ladda.create(element)來取得物件
呼叫物件的start來開始動畫
呼叫物件的stop來停止動畫
<div><pre class="brush:javascript">$(function () {
    $("#btn1").click(function () {
        var obj = Ladda.create(this);
        obj.start();
        setTimeout(function () {
            obj.stop();
        }, 1000);
    });
});
</pre></div>
spin.js.2.0.1好像和ladda不太和，最好先降到spin.js 1.3版就好

<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="300" src="http://jsfiddle.net/1fda8zcj/embedded/result,html,js" width="100%"></iframe></div>

相關資料
[Bootstrap button loading text](http://blog.developer.idv.tw/2014/10/bootstrap-button-loading-text.html)
[http://blog.developer.idv.tw/2014/10/bootstrap-button-loading-text.html](http://blog.developer.idv.tw/2014/10/bootstrap-button-loading-text.html)

[spin.js 套件](http://blog.developer.idv.tw/2014/10/spinjs.html)
[http://blog.developer.idv.tw/2014/10/spinjs.html](http://blog.developer.idv.tw/2014/10/spinjs.html)