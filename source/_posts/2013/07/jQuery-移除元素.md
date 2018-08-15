---
title: jQuery 移除元素
tags:
  - jQuery
date: 2013-07-29 18:15:00
---

<div><table border="1"><tbody><tr>            <td>.detach()</td>            <td>移除符合指定的選擇器元素，包含選擇器本身
被移除的元素原本繫結的事件，還原回去後並不會消失</td>        </tr><tr>            <td>.empty()</td>            <td>移除符合指定的選擇器元素，不包含選擇器本身
被移除的元素原本繫結的事件，還原回去後並不會消失</td>        </tr><tr>            <td>.remove()</td>            <td>移除符合指定的選擇器元素，包含選擇器本身
被移除的元素原本繫結的事件，還原回去後會消失</td>        </tr><tr>            <td>.unwrap()</td>            <td>移除符合指定的選擇器外層元素</td>        </tr></tbody></table></div>
<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="500" src="http://jsfiddle.net/c6zY2/embedded/js,html,css,result/presentation" width="100%"></iframe></div>