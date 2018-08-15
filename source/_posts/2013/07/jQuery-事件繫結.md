---
title: jQuery 事件繫結
tags:
  - jQuery
date: 2013-07-25 15:48:00
---

<div><table border="1"><tbody><tr>            <td>.bind()</td>            <td>為一個元素綁定一個事件處理
執行多次會重覆綁定
動態生成元素綁定事件會有先後問題</td>        </tr><tr>            <td>.unbind()</td>            <td>從元素上移除一個之前綁定的事件處理</td>        </tr><tr>            <td>.live()</td>            <td>附加一個事件處理器到指定選擇器的元素上
version deprecated:1.7, remove:1.9</td>        </tr><tr>            <td>.die()</td>            <td>從元素移除之前用.live()綁定的事件
version deprecated:1.7, remove:1.9</td>        </tr><tr>            <td>.delegate()</td>            <td>指派事件處理
利用事件的Bubble Up特性，在上層元素掛上事件處理
V1.4.2以上適用</td>        </tr><tr>            <td>.undelegate()</td>            <td>解除事件指派
V1.4.2以上適用</td>        </tr><tr>            <td>.on()</td>            <td>繫結事件
v1.7以上適用</td>        </tr><tr>            <td>.off()</td>            <td>解除事件
v1.7以上適用</td>        </tr><tr>            <td>.trigger()</td>            <td>觸發事件</td>        </tr><tr>            <td>.one()</td>            <td>在元素上綁定一個事件處理函式
該處理函式只會執行一次，然後刪除自已</td>        </tr></tbody></table></div>
<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="500" src="http://jsfiddle.net/KMQun/embedded/js,html,result/presentation" width="100%"></iframe></div>