---
title: StyleCop SA1208 排列Using時先放置System指示詞
tags:
  - 'C#'
  - StyleCop
date: 2016-06-07 14:12:00
---

在使用組合管理Using-&gt;移除並排序Using功能的時後，會依照字母的順序排序
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-4_luDR6yqzk/V1Zluu_U-5I/AAAAAAAADyg/peZgQ-8DWE80Jz07KFQ_5hDzB6sP7lTuQCLcB/s1600/01.png)](https://2.bp.blogspot.com/-4_luDR6yqzk/V1Zluu_U-5I/AAAAAAAADyg/peZgQ-8DWE80Jz07KFQ_5hDzB6sP7lTuQCLcB/s1600/01.png)</div>

StyleCop就會靠北說System開頭的命名空間要放在最上面
SA1208 : CSharp.Ordering : System using directives must be placed before all other using directives
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-y1iOIfsjlRs/V1Zlup2ZRuI/AAAAAAAADyc/p7rBuW9mtIYgN1bjbykZ3JXbyjq2wYlpwCLcB/s1600/02.png)](https://1.bp.blogspot.com/-y1iOIfsjlRs/V1Zlup2ZRuI/AAAAAAAADyc/p7rBuW9mtIYgN1bjbykZ3JXbyjq2wYlpwCLcB/s1600/02.png)</div>

工具-&gt;選項-&gt;文字編輯器-&gt;C#-&gt;進階-
排序Usning時先放置System指示詞勾起來就行了
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-bhudH420YNY/V1ZluZlssBI/AAAAAAAADyk/BpBx5WxHOb0Krwwp0xmeWQiieeBMV4DsACLcB/s1600/03.png)](https://1.bp.blogspot.com/-bhudH420YNY/V1ZluZlssBI/AAAAAAAADyk/BpBx5WxHOb0Krwwp0xmeWQiieeBMV4DsACLcB/s1600/03.png)</div>