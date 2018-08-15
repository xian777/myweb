---
title: jQuery 全域事件處理
tags:
  - jQuery
date: 2013-08-01 14:09:00
---

<div>jQuery v1.8之後，ajax全域事件只能綁定到document元素</div>
<div><table border="1"><tbody><tr>            <td>.ajaxStart()</td>            <td>ajax要求開始</td>        </tr><tr>            <td>.ajaxSend(event, jqXHR, ajaxOptions)</td>            <td>發出ajax要求</td>        </tr><tr>            <td>.ajaxSuccess(event, jqXHR, ajaxOptions, ThrownError)</td>            <td>ajax要求成功的話就觸發這個事件</td>        </tr><tr>            <td>.ajaxError(event, XMLHttpRequest, ajaxOptions)</td>            <td>ajax要求失敗的話就觸發這個事件</td>        </tr><tr>            <td>.ajaxComplete(event, XMLHttpRequest, ajaxOptions)</td>            <td>ajax要求完成</td>        </tr><tr>            <td>.ajaxStop()</td>            <td>ajax要求結束</td>        </tr></tbody></table></div>
<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="500" src="http://jsfiddle.net/mcXNu/embedded/js,html,result/presentation" width="100%"></iframe></div>