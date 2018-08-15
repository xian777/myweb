---
title: jQuery Ajax呼叫方式
tags:
  - jQuery
date: 2013-08-01 17:06:00
---

<div>.ajax({})為底層呼叫方式，參數如下
.ajaxSetup()則是用來設定參數的預設值</div>
<div><table border="1"><tbody><tr>            <td>url</td>            <td>請求的URL</td>        </tr><tr>            <td>type</td>            <td>請求的方式，例如POST或是GET</td>        </tr><tr>            <td>data</td>            <td>請求的參數</td>        </tr><tr>            <td>dataType</td>            <td>指定回應的格式，有以下幾種格式
xml, html, json, jsonp, script, text</td>        </tr><tr>            <td>timeout</td>            <td>逾時的毫秒數，如果超出設定的時間，就會觸發error設定的callback函式</td>        </tr><tr>            <td>global</td>            <td>設定是否要觸發全域事件處理，啟用為true, 停用為false
預設是啟用狀態</td>        </tr><tr>            <td>contentType</td>            <td>指定請求的內容類型
預設為application/x-www-form-urlencoded，和表單發送的類型一樣</td>        </tr><tr>            <td>success</td>            <td>請求成功時呼叫的函式</td>        </tr><tr>            <td>error</td>            <td>請求失敗時呼叫的函式</td>        </tr><tr>            <td>complete</td>            <td>整個請求完成時呼叫的函式</td>        </tr><tr>            <td>beforeSend</td>            <td>發出請求之前呼叫的函式
可以用來執行請求前的操作，例如自訂標頭</td>        </tr><tr>            <td>urlasync</td>            <td>非同步為true, 同步為false
預設是非同步</td>        </tr><tr>            <td>processData</td>            <td>是否對傳送的資料做URL編碼，true為編碼，false為不編碼
預設是會編碼</td>        </tr><tr>            <td>ifModified</td>            <td>根據標頭的Last-Modified來判斷是否更新
預設為不檢查標頭</td>        </tr></tbody></table></div>
<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="500" src="http://jsfiddle.net/mJGQF/embedded/js,html,result/presentation" width="100%"></iframe></div>