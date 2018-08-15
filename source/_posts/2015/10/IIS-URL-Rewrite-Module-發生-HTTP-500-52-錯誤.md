---
title: IIS URL Rewrite Module 發生 HTTP 500.52 錯誤
tags:
  - iis
date: 2015-10-09 11:43:00
---

最近使用的IIS URL Rewrite模組發生了500.52錯誤
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-zQUJWNA4ux8/Vhc3eXjlngI/AAAAAAAACkc/VpadeJYWBQQ/s1600/0.500.52.png)](http://2.bp.blogspot.com/-zQUJWNA4ux8/Vhc3eXjlngI/AAAAAAAACkc/VpadeJYWBQQ/s1600/0.500.52.png)</div>

看起來像是NTFS權限的問題，把IIS_IUSR帳號加入後，錯誤訊息又變了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-ryedzB87MxI/Vhc3qXqAXSI/AAAAAAAACkk/3x1fBsCo3I4/s1600/0.500.52-1.png)](http://3.bp.blogspot.com/-ryedzB87MxI/Vhc3qXqAXSI/AAAAAAAACkk/3x1fBsCo3I4/s1600/0.500.52-1.png)</div>
在URL Rewrite的時後，把HTTP_ACCEPT_ENCODING設定空就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-4Vr_72byhB0/Vhc3t2AtRdI/AAAAAAAACks/aPnouMLaX4M/s1600/remove.png)](http://3.bp.blogspot.com/-4Vr_72byhB0/Vhc3t2AtRdI/AAAAAAAACks/aPnouMLaX4M/s1600/remove.png)</div>
另一個方式是把IIS的動態壓縮關閉

[![](http://1.bp.blogspot.com/-fP1JvNXmzoc/Vhc3ty7x5uI/AAAAAAAACk0/eKU4LRYJ9PI/s1600/10.%25E5%25A3%2593%25E7%25B8%25AE.png)](http://1.bp.blogspot.com/-fP1JvNXmzoc/Vhc3ty7x5uI/AAAAAAAACk0/eKU4LRYJ9PI/s1600/10.%25E5%25A3%2593%25E7%25B8%25AE.png)關閉動態壓縮
[![](http://1.bp.blogspot.com/-MRzmDIKgR9Q/Vhc3tzGAS9I/AAAAAAAACkw/w5jq7KY5d_E/s1600/11.%25E5%258B%2595%25E6%2585%258B%25E5%25A3%2593%25E7%25B8%25AE.png)](http://1.bp.blogspot.com/-MRzmDIKgR9Q/Vhc3tzGAS9I/AAAAAAAACkw/w5jq7KY5d_E/s1600/11.%25E5%258B%2595%25E6%2585%258B%25E5%25A3%2593%25E7%25B8%25AE.png)