---
title: jQuery 層級選擇器
tags:
  - jQuery
date: 2013-07-12 13:54:00
---

<div><table border="1">                <tbody><tr>                        <td colspan="2">層級選擇器</td>                    </tr><tr>                        <td>範例</td>                        <td>說明</td>                    </tr><tr>                        <td>$("E F")</td>                        <td>後代選擇器，找出在E元素的所有子元素裡面的所有F元素
遞迴子元素的子元素，效率較差 </td>                    </tr><tr>                        <td>$("E&gt;F")</td>                        <td>子代選擇器，找出在E元素的第一層子元素中的所有F元素
只找子元素，效能較佳 </td>                    </tr><tr>                        <td>$("E+F")</td>                        <td>毗鄰選擇器，E元素之後同層級的第一個F元素</td>                    </tr><tr>                        <td>$("E~F")</td>                        <td>鄰後選擇器，E元素之後同層級的所有F元素</td>                    </tr></tbody>            </table></div>
<div><iframe allowfullscreen="allowfullscreen" frameborder="0" height="500" src="http://jsfiddle.net/73pfG/embedded/js,html,result/presentation" width="100%"></iframe></div>