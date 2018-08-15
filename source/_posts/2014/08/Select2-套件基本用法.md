---
title: Select2 套件基本用法
tags:
  - ASP.NET
  - NuGet
  - Select2
date: 2014-08-22 14:43:00
---

Select2 套件是一個加強下拉選單的套件，官網提供了許多詳細的示範
這裡用一個簡單的例子來介紹這個套件
首先開一個Web專案
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/--1rBcMtW1Y0/U_bkynIQwNI/AAAAAAAABic/OlnDplvnK8I/s1600/01.%E9%96%8B%E5%B0%88%E6%A1%88.png)](http://3.bp.blogspot.com/--1rBcMtW1Y0/U_bkynIQwNI/AAAAAAAABic/OlnDplvnK8I/s1600/01.%E9%96%8B%E5%B0%88%E6%A1%88.png)</div>
用一個html頁面來練習
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ToVRuf067nQ/U_bk416LpLI/AAAAAAAABik/Nsn2uLwtv3E/s1600/02.%E6%96%B0%E5%A2%9E%E9%A0%81%E9%9D%A2.png)](http://2.bp.blogspot.com/-ToVRuf067nQ/U_bk416LpLI/AAAAAAAABik/Nsn2uLwtv3E/s1600/02.%E6%96%B0%E5%A2%9E%E9%A0%81%E9%9D%A2.png)</div>
透過NuGet新增select2.js套件
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-LsOCKW5DqQc/U_bk_S6qg0I/AAAAAAAABis/y5G7T6NOi9U/s1600/03.select2%E5%A5%97%E4%BB%B6.png)](http://1.bp.blogspot.com/-LsOCKW5DqQc/U_bk_S6qg0I/AAAAAAAABis/y5G7T6NOi9U/s1600/03.select2%E5%A5%97%E4%BB%B6.png)</div>
select2.js套件包含了CSS和JavaScript和語系
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Hy2TdLfmd7s/U_blD22Tm9I/AAAAAAAABi0/vvZC8707Vl4/s1600/04.%E6%AA%94%E6%A1%88%E7%B5%90%E6%A7%8B.png)](http://4.bp.blogspot.com/-Hy2TdLfmd7s/U_blD22Tm9I/AAAAAAAABi0/vvZC8707Vl4/s1600/04.%E6%AA%94%E6%A1%88%E7%B5%90%E6%A7%8B.png)</div>
在html裡面引用CSS和JavaScript，該套件相依於JQuery，最低版本1.7以上
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-lKdMrr5EHxA/U_blHcBAGQI/AAAAAAAABi8/9EF63xjvhCc/s1600/05.%E5%BC%95%E5%85%A5%E6%AA%94%E6%A1%88.png)](http://4.bp.blogspot.com/-lKdMrr5EHxA/U_blHcBAGQI/AAAAAAAABi8/9EF63xjvhCc/s1600/05.%E5%BC%95%E5%85%A5%E6%AA%94%E6%A1%88.png)</div>
手動輸入一個下拉選單
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-pz9TUisEjcc/U_blLbXR6jI/AAAAAAAABjE/4VypAffM6h8/s1600/06.%E5%8A%A0%E5%85%A5%E4%B8%8B%E6%8B%89%E9%81%B8%E5%96%AE.png)](http://1.bp.blogspot.com/-pz9TUisEjcc/U_blLbXR6jI/AAAAAAAABjE/4VypAffM6h8/s1600/06.%E5%8A%A0%E5%85%A5%E4%B8%8B%E6%8B%89%E9%81%B8%E5%96%AE.png)</div>
一般的下拉選單看起來像這個樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-rXD3i6ufPks/U_blO9ka_eI/AAAAAAAABjM/WNgZSkYrBF4/s1600/07.%E4%B8%8B%E6%8B%89%E9%81%B8%E5%96%AE%E7%9A%84%E6%A8%A3%E5%AD%90.png)](http://3.bp.blogspot.com/-rXD3i6ufPks/U_blO9ka_eI/AAAAAAAABjM/WNgZSkYrBF4/s1600/07.%E4%B8%8B%E6%8B%89%E9%81%B8%E5%96%AE%E7%9A%84%E6%A8%A3%E5%AD%90.png)</div>
透過JQuery啟用select2
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-GBLzgQcd89M/U_blSWWuvlI/AAAAAAAABjU/KBZSwC8Jd2o/s1600/08.%E5%8A%A0%E5%85%A5JQuery.png)](http://4.bp.blogspot.com/-GBLzgQcd89M/U_blSWWuvlI/AAAAAAAABjU/KBZSwC8Jd2o/s1600/08.%E5%8A%A0%E5%85%A5JQuery.png)</div>
看起來漂亮多了，而已還有查詢過濾的功能
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-EoqcBDY_4Ho/U_blWRJoSyI/AAAAAAAABjc/xnp3Qs6hpmg/s1600/09.%E5%A5%97%E4%BB%B6select2%E7%9A%84%E6%A8%A3%E5%AD%90.png)](http://1.bp.blogspot.com/-EoqcBDY_4Ho/U_blWRJoSyI/AAAAAAAABjc/xnp3Qs6hpmg/s1600/09.%E5%A5%97%E4%BB%B6select2%E7%9A%84%E6%A8%A3%E5%AD%90.png)</div>
加入多選屬性
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-BRgdJ_TQ1lI/U_blaO3szHI/AAAAAAAABjk/reLmSAgoFe0/s1600/10.%E5%8A%A0%E5%85%A5%E5%A4%9A%E9%81%B8.png)](http://3.bp.blogspot.com/-BRgdJ_TQ1lI/U_blaO3szHI/AAAAAAAABjk/reLmSAgoFe0/s1600/10.%E5%8A%A0%E5%85%A5%E5%A4%9A%E9%81%B8.png)</div>
Select2套件的多選功能
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-5tm6ArFLpfI/U_bld8UpKyI/AAAAAAAABjs/Nha7t2csK6M/s1600/11.%E5%A4%9A%E9%81%B8%E7%9A%84%E6%A8%A3%E5%AD%90.png)](http://1.bp.blogspot.com/-5tm6ArFLpfI/U_bld8UpKyI/AAAAAAAABjs/Nha7t2csK6M/s1600/11.%E5%A4%9A%E9%81%B8%E7%9A%84%E6%A8%A3%E5%AD%90.png)</div>
參考資料

[Select2 官網](http://ivaynberg.github.io/select2/)

[Select 2 CDN](http://zh-tw.cdnjs.com/libraries/select2)

[Select2 Bootstrap 3 CSS](http://fk.github.io/select2-bootstrap-css/)