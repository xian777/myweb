---
title: TeamCity整合FxCop報表
tags:
  - FxCop
  - TeamCity
date: 2014-04-22 14:37:00
---

<div>FxCop 10的安裝檔在Microsoft Windows SDK中，所以首先要先下載[Windwos SDK](http://www.microsoft.com/en-us/download/details.aspx?displaylang=en&amp;id=8279)</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Ryzi5Wp1mxk/U1YM8QFNVeI/AAAAAAAABQY/o5yi63VDzdE/s1600/00.FxCop%E8%BC%89%E9%BB%9E.png)](http://2.bp.blogspot.com/-Ryzi5Wp1mxk/U1YM8QFNVeI/AAAAAAAABQY/o5yi63VDzdE/s1600/00.FxCop%E8%BC%89%E9%BB%9E.png)</div>
<div>SDK安裝好後，安裝檔的路徑在C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\FXCop\FxCopSetup.exe</div>由於VS2013已整合FxCop 12版，所以這裡以FxCop 12版為例
<div>安裝好VS2013後，FxCop執行檔的路徑在
FxCop的路徑在C:\Program Files (x86)\Microsoft Visual Studio 12.0\Team Tools\Static Analysis Tools\FxCop</div>
<div>在Build Step中新增一個FxCop Runner</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-UPextgdfaqg/U1YNNQYcR0I/AAAAAAAABQg/dl-bnwC9fPQ/s1600/02.%E6%96%B0%E5%A2%9EFxCop.png)](http://1.bp.blogspot.com/-UPextgdfaqg/U1YNNQYcR0I/AAAAAAAABQg/dl-bnwC9fPQ/s1600/02.%E6%96%B0%E5%A2%9EFxCop.png)</div>
<div>設定內容主要是指定FxCop執行檔的路徑
和要分析的Assembly檔案位置
C:\Program Files (x86)\Microsoft Visual Studio 12.0\Team Tools\Static Analysis Tools\FxCop
比較方便的方式是到Build Agent上面設定buildAgent.properties加入
system.FxCopRoot=C\:\\Program Files (x86)\\Microsoft Visual Studio 12.0\\Team Tools\\Static Analysis Tools\\FxCop
就可以用Autodetect而不用指定路徑了
P.S. 注意跳脫符號

</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-IxO1nBWwCG4/U1YOJCl6c8I/AAAAAAAABQ4/PJnb62unAG0/s1600/03.FxCop%E5%BB%BA%E7%BD%AE%E8%A8%AD%E5%AE%9A.png)](http://4.bp.blogspot.com/-IxO1nBWwCG4/U1YOJCl6c8I/AAAAAAAABQ4/PJnb62unAG0/s1600/03.FxCop%E5%BB%BA%E7%BD%AE%E8%A8%AD%E5%AE%9A.png)</div>建置成功後就會多出一個FxCop的數據
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-hRYlHqjQsss/U1YR362allI/AAAAAAAABRM/DZZnNx-VHR4/s1600/05.%E7%B8%BD%E8%A1%A8.png)](http://3.bp.blogspot.com/-hRYlHqjQsss/U1YR362allI/AAAAAAAABRM/DZZnNx-VHR4/s1600/05.%E7%B8%BD%E8%A1%A8.png)</div><div>點擊連結或是右上角的Code Inspection就會轉入FxCop報表的詳細頁面</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-5dyGrZH_Lwo/U1YOMJfd2rI/AAAAAAAABRA/3JONiZpg7o8/s1600/04.%E5%BB%BA%E7%BD%AE%E5%A0%B1%E8%A1%A8.png)](http://4.bp.blogspot.com/-5dyGrZH_Lwo/U1YOMJfd2rI/AAAAAAAABRA/3JONiZpg7o8/s1600/04.%E5%BB%BA%E7%BD%AE%E5%A0%B1%E8%A1%A8.png)</div>
<div>
</div>