---
title: Gogs with nginx reverse proxy
tags:
  - gogs
  - nginx
date: 2016-08-15 21:37:00
---

ngix新增一組站台設定
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-5pCqX-PKlL4/V7HFi9H5m_I/AAAAAAAAD2w/IlMP7TcMxdUbPpXy_r1Gv5Ywnmn8Vv6QgCLcB/s1600/01.png)](https://3.bp.blogspot.com/-5pCqX-PKlL4/V7HFi9H5m_I/AAAAAAAAD2w/IlMP7TcMxdUbPpXy_r1Gv5Ywnmn8Vv6QgCLcB/s1600/01.png)</div>
新增站台的DNS，為了測試方便所以建在本機的hosts
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-TKZboAubPcE/V7HFi3IQVxI/AAAAAAAAD20/aj4gq2qUzj08cHpfG8nN6GH6KPotK515gCLcB/s1600/02.png)](https://2.bp.blogspot.com/-TKZboAubPcE/V7HFi3IQVxI/AAAAAAAAD20/aj4gq2qUzj08cHpfG8nN6GH6KPotK515gCLcB/s1600/02.png)</div>
修改一下gogs的設定，把domain和ROOT_URL改成這組測試的網址
順便DISABLE_SSH = true
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-NWt0cLVNSD8/V7HFi-bF8RI/AAAAAAAAD2s/Z4GJ4sS8QyU6bgG1XPAbOIqV4LOyYj9ogCLcB/s1600/03.png)](https://3.bp.blogspot.com/-NWt0cLVNSD8/V7HFi-bF8RI/AAAAAAAAD2s/Z4GJ4sS8QyU6bgG1XPAbOIqV4LOyYj9ogCLcB/s1600/03.png)</div>
重新啟動gogs服務後，就可以用這組測試網址了
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-_ejX-3n9d10/V7HFjXs0YCI/AAAAAAAAD24/C8_75LtckZY6qaY2SE7fxLQEVJJIfEIQQCLcB/s1600/04.png)](https://4.bp.blogspot.com/-_ejX-3n9d10/V7HFjXs0YCI/AAAAAAAAD24/C8_75LtckZY6qaY2SE7fxLQEVJJIfEIQQCLcB/s1600/04.png)</div>