---
title: jQuery 屬性操作
tags:
  - jQuery
date: 2013-07-30 10:49:00
---

<div><table border="1"><tbody><tr>            <td>.attr()</td>            <td>取得或設定屬性</td>        </tr><tr>            <td>.removeAttr()</td>            <td>移除屬性</td>        </tr><tr>            <td>.prop()</td>            <td>取得或設定屬性</td>        </tr><tr>            <td>.removeProp()</td>            <td>移除屬性</td>        </tr></tbody></table></div>
<div>.attr()和.prop()的差異在1.6版本
對於bool值的屬性，例如checked, disabled, readonly, selected...，用prop會比較合適</div>
<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="500" src="http://jsfiddle.net/9hJqP/embedded/js,html,result/presentation" width="100%"></iframe></div>