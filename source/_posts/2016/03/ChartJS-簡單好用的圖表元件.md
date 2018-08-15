---
title: ChartJS 簡單好用的圖表元件
tags:
  - NuGet套件
date: 2016-03-19 11:36:00
---

正所謂一圖解千文，一張圖表可以更容易地看出資料背後所代表的意義
ChartJS是一套簡單好用基於HTML5的JS Library，提供六種圖表，使用方式還滿簡單地

首先透過Nuget或Bower取得ChartJS
<div><pre class="brush:bash">$ Install-Package Chart.js
$ Bower Install Chart.js
</pre></div>
<div>宣告一個canvas元素 
<pre class="brush:html">&lt;canvas id="myLine" width="300" height="400"&gt;&lt;/canvas&gt;
</pre></div>
<div>準備該適合該圖表的資料
把資料傳入該圖表即可 </div><div><pre class="brush:javascript">(function () {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var lineChartData = {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; labels: ["January", "February", "March", "April", "May", "June", "July"],

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; datasets: [

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fillColor: "rgba(220,220,220,0.5)",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; strokeColor: "rgba(220,220,220,1)",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pointColor: "rgba(220,220,220,1)",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pointStrokeColor: "#fff",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data: [65, 59, 90, 81, 56, 55, 40]

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fillColor: "rgba(151,187,205,0.5)",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; strokeColor: "rgba(151,187,205,1)",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pointColor: "rgba(151,187,205,1)",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pointStrokeColor: "#fff",

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; data: [28, 48, 40, 19, 96, 27, 100]

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ]

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var ctx = document.getElementById("myLine").getContext("2d");

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var myLine = new Chart(ctx).Line(lineChartData);

&nbsp; &nbsp; &nbsp; &nbsp; })();
</pre></div>

<div>[ChartJS官網](http://www.chartjs.org/)</div>