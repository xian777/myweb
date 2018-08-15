---
title: SVN Global Ignore
tags: []
date: 2014-06-04 15:16:00
---

首先是全域設定檔，位置在%AppData%\Subversion\config
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-FM871yMVeAk/U47GlEqY72I/AAAAAAAABYU/64h9gk3UKdA/s1600/01.AppData.png)](http://2.bp.blogspot.com/-FM871yMVeAk/U47GlEqY72I/AAAAAAAABYU/64h9gk3UKdA/s1600/01.AppData.png)</div>
搜尋global-ignores可以找到用空白做分隔符號的定義，把前面的註解拿掉就啟用了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-pFLsgz-iI1g/U47Gp5yQy-I/AAAAAAAABYc/oXGRy_TdFlU/s1600/02.%E5%85%A8%E5%9F%9F%E8%A8%AD%E5%AE%9A%E6%AA%94.png)](http://3.bp.blogspot.com/-pFLsgz-iI1g/U47Gp5yQy-I/AAAAAAAABYc/oXGRy_TdFlU/s1600/02.%E5%85%A8%E5%9F%9F%E8%A8%AD%E5%AE%9A%E6%AA%94.png)</div>
第二個地方是TortoiseSVN的設定
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-EAFVkbWuhgc/U47G0IU_feI/AAAAAAAABYk/KqVOEaHncNw/s1600/03.%E8%A8%AD%E5%AE%9A.png)](http://4.bp.blogspot.com/-EAFVkbWuhgc/U47G0IU_feI/AAAAAAAABYk/KqVOEaHncNw/s1600/03.%E8%A8%AD%E5%AE%9A.png)</div>
一樣是用空白做分隔符號的定義，如果全域設定檔啟用，將會覆蓋掉這裡的功能
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-6sryhUbg0_s/U47G339iAhI/AAAAAAAABYs/HyHpafPFSqs/s1600/04.%E8%A8%AD%E5%AE%9A%E5%AE%9A%E7%BE%A9.png)](http://4.bp.blogspot.com/-6sryhUbg0_s/U47G339iAhI/AAAAAAAABYs/HyHpafPFSqs/s1600/04.%E8%A8%AD%E5%AE%9A%E5%AE%9A%E7%BE%A9.png)</div>
第三個地方在專案上，透過TortoiseSVN的屬性來設定比較簡單
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-lnqmV1M5DBA/U47HF3bufYI/AAAAAAAABY0/6zOSvVNAkpI/s1600/05.%E5%B1%AC%E6%80%A7.png)](http://3.bp.blogspot.com/-lnqmV1M5DBA/U47HF3bufYI/AAAAAAAABY0/6zOSvVNAkpI/s1600/05.%E5%B1%AC%E6%80%A7.png)</div>

如果沒設定過的話，需要手動新增一個設定
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-LElnfs052J8/U47HLdv-_vI/AAAAAAAABY8/2GVqjqwcQSc/s1600/06.%E6%96%B0%E5%A2%9E%E5%B1%AC%E6%80%A7.png)](http://4.bp.blogspot.com/-LElnfs052J8/U47HLdv-_vI/AAAAAAAABY8/2GVqjqwcQSc/s1600/06.%E6%96%B0%E5%A2%9E%E5%B1%AC%E6%80%A7.png)</div>
有svn:global-ignores的屬性可以設定，每一行代表一個設定
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-YXgcpmrROFs/U47HVQpk0TI/AAAAAAAABZE/Z97mqy1K5tY/s1600/07.GlobalIgnore.png)](http://3.bp.blogspot.com/-YXgcpmrROFs/U47HVQpk0TI/AAAAAAAABZE/Z97mqy1K5tY/s1600/07.GlobalIgnore.png)</div>

C#常用的忽略列表有
<div><pre class="brush:shell">#OS junk files
[Tt]humbs.db

#Visual Studio files
[Bb]in
[Oo]bj
*.user
*.suo
*.[Cc]ache

#NuGet
packages
*.nupkg

# SQL Server files
*.mdf
*.ldf
</pre></div>