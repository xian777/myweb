---
title: TeamCity整合Code Coverage報表
tags:
  - Code Coverage
  - TeamCity
date: 2014-04-22 17:04:00
---

<div>首先加入一個MSTest的Build Step</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-mFAFpZ4sBFg/U1Yv105qBlI/AAAAAAAABRc/HCJbfbaCuIw/s1600/01.%E6%96%B0%E5%A2%9ERunner.png)](http://2.bp.blogspot.com/-mFAFpZ4sBFg/U1Yv105qBlI/AAAAAAAABRc/HCJbfbaCuIw/s1600/01.%E6%96%B0%E5%A2%9ERunner.png)</div>
<div>這裡以VS2013為例，選擇要執行單元測試的專案元件</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-aFtWBsGltzs/U1dz2eGt4YI/AAAAAAAABT4/rKk7WdWI9H0/s1600/02.%E5%8A%A0%E5%85%A5%E6%B8%AC%E8%A9%A6%E5%85%83%E4%BB%B6.png)](http://3.bp.blogspot.com/-aFtWBsGltzs/U1dz2eGt4YI/AAAAAAAABT4/rKk7WdWI9H0/s1600/02.%E5%8A%A0%E5%85%A5%E6%B8%AC%E8%A9%A6%E5%85%83%E4%BB%B6.png)</div>
<div>拉到最下面後可以選擇Code Coverage的工具，這裡以dotCover為例子</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Xjc2zO5sAZ8/U1Yv-WpsCNI/AAAAAAAABRs/oXxgjTphKRk/s1600/03.%E9%81%B8%E6%93%87dotCover.png)](http://2.bp.blogspot.com/-Xjc2zO5sAZ8/U1Yv-WpsCNI/AAAAAAAABRs/oXxgjTphKRk/s1600/03.%E9%81%B8%E6%93%87dotCover.png)</div>
<div>主要就是輸入Filter，+:加入，-:排除，注意不用輸入副檔名</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Q9E4eWUXyxI/U1YwCuFlBkI/AAAAAAAABR0/-LWyBvHrEgI/s1600/04.%E5%8A%A0%E5%85%A5Conver%E5%85%83%E4%BB%B6.png)](http://3.bp.blogspot.com/-Q9E4eWUXyxI/U1YwCuFlBkI/AAAAAAAABR0/-LWyBvHrEgI/s1600/04.%E5%8A%A0%E5%85%A5Conver%E5%85%83%E4%BB%B6.png)</div>
<div>建置成功後就會看到單元測試覆蓋率的報表了 </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-0i27A5sdKdM/U1YwGCyP0pI/AAAAAAAABR8/jIVmKdLPs4A/s1600/05.%E7%B8%BD%E8%A1%A8.png)](http://1.bp.blogspot.com/-0i27A5sdKdM/U1YwGCyP0pI/AAAAAAAABR8/jIVmKdLPs4A/s1600/05.%E7%B8%BD%E8%A1%A8.png)</div>