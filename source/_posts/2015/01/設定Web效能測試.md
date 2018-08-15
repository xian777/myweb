---
title: 設定Web效能測試
tags: []
date: 2015-01-05 16:58:00
---

加入Web效能測試
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-99mTrr1aW0E/VKpRqk4NanI/AAAAAAAACFU/jtUa3AD_VSI/s1600/01.%E5%8A%A0%E5%85%A5Web%E6%95%88%E8%83%BD%E6%B8%AC%E8%A9%A6.png)](http://3.bp.blogspot.com/-99mTrr1aW0E/VKpRqk4NanI/AAAAAAAACFU/jtUa3AD_VSI/s1600/01.%E5%8A%A0%E5%85%A5Web%E6%95%88%E8%83%BD%E6%B8%AC%E8%A9%A6.png)</div>
如果看到這個錯誤訊息，是IE瀏覽器的安全性設定造成的
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-84QcGZADseI/VKpRqofSrwI/AAAAAAAACFQ/JB1bFtf5hY8/s1600/02.%E9%8C%AF%E8%AA%A4%E8%A8%8A%E6%81%AF.png)](http://1.bp.blogspot.com/-84QcGZADseI/VKpRqofSrwI/AAAAAAAACFQ/JB1bFtf5hY8/s1600/02.%E9%8C%AF%E8%AA%A4%E8%A8%8A%E6%81%AF.png)</div>
在伺服器管理員中，點擊設定IE ESC
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-MZfXDAqyvBc/VKpRqs8nfgI/AAAAAAAACG0/tjBlcvf3Hjo/s1600/03.%E8%A8%AD%E5%AE%9AIPSEC.png)](http://1.bp.blogspot.com/-MZfXDAqyvBc/VKpRqs8nfgI/AAAAAAAACG0/tjBlcvf3Hjo/s1600/03.%E8%A8%AD%E5%AE%9AIPSEC.png)</div>
把管理員關閉就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-ZhlQ7fy2yiw/VKpRre9ss7I/AAAAAAAACFY/XkUO18Sq1uQ/s1600/04.%E9%97%9C%E9%96%89IEESC.png)](http://1.bp.blogspot.com/-ZhlQ7fy2yiw/VKpRre9ss7I/AAAAAAAACFY/XkUO18Sq1uQ/s1600/04.%E9%97%9C%E9%96%89IEESC.png)</div>
在瀏覽器中就會看到錄製工具列
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-tzqsSLuwYJk/VKpRr5q0GRI/AAAAAAAACFo/W_mY-yuBNyw/s1600/05.%E5%95%9F%E5%8B%95%E9%8C%84%E8%A3%BD.png)](http://1.bp.blogspot.com/-tzqsSLuwYJk/VKpRr5q0GRI/AAAAAAAACFo/W_mY-yuBNyw/s1600/05.%E5%95%9F%E5%8B%95%E9%8C%84%E8%A3%BD.png)</div>
在網址列隨便輸入網址，就會看到自動錄製操作
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-1EOx8cWF8GU/VKpRsNU-DRI/AAAAAAAACFk/rxeL1Zw64-A/s1600/06.%E9%8C%84%E8%A3%BD%E7%B6%B2%E7%AB%99.png)](http://3.bp.blogspot.com/-1EOx8cWF8GU/VKpRsNU-DRI/AAAAAAAACFk/rxeL1Zw64-A/s1600/06.%E9%8C%84%E8%A3%BD%E7%B6%B2%E7%AB%99.png)</div>
按下停止錄制後，會把錄製的結果帶回Visual Studio
可以在已錄制的項目上按屬性來修改，也可以手動插入要求
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-PK4J7p0omYg/VKpRs3_SppI/AAAAAAAACFw/FGnJmsjXaYY/s1600/07.%E5%AE%8C%E6%88%90%E9%8C%84%E8%A3%BD.png)](http://2.bp.blogspot.com/-PK4J7p0omYg/VKpRs3_SppI/AAAAAAAACFw/FGnJmsjXaYY/s1600/07.%E5%AE%8C%E6%88%90%E9%8C%84%E8%A3%BD.png)</div>
接下來介紹如果繫結資料，先準備一個XML檔案
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-0MH-lgCwCEY/VKpRtGpLDgI/AAAAAAAACF0/AFxHizxeqAg/s1600/09.%E5%8A%A0%E5%85%A5XML%E6%AA%94%E6%A1%88.png)](http://1.bp.blogspot.com/-0MH-lgCwCEY/VKpRtGpLDgI/AAAAAAAACF0/AFxHizxeqAg/s1600/09.%E5%8A%A0%E5%85%A5XML%E6%AA%94%E6%A1%88.png)</div>
隨便輸入一些資料
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;customers&gt;
  &lt;customer account="aa" /&gt;
  &lt;customer account="bb" /&gt;
  &lt;customer account="cc" /&gt;
&lt;/customers&gt;
</pre></div>
點擊新增資料來源
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-QVj9WMnCJxI/VKpRtoT1jLI/AAAAAAAACF8/KoMtf1AGp6I/s1600/10.%E5%8A%A0%E5%85%A5%E8%B3%87%E6%96%99%E4%BE%86%E6%BA%90.png)](http://4.bp.blogspot.com/-QVj9WMnCJxI/VKpRtoT1jLI/AAAAAAAACF8/KoMtf1AGp6I/s1600/10.%E5%8A%A0%E5%85%A5%E8%B3%87%E6%96%99%E4%BE%86%E6%BA%90.png)</div>
選擇剛準備的XML檔案，可以看到解析出來的資料
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-R9xhLdiaeNc/VKpRuL1mIMI/AAAAAAAACGA/709r1p509Rs/s1600/11.%E5%B0%8D%E6%87%89xml%E6%AA%94%E6%A1%88.png)](http://1.bp.blogspot.com/-R9xhLdiaeNc/VKpRuL1mIMI/AAAAAAAACGA/709r1p509Rs/s1600/11.%E5%B0%8D%E6%87%89xml%E6%AA%94%E6%A1%88.png)</div>
選擇資料來源的資料表
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-LRgNR0Iac18/VKpRuk2t4mI/AAAAAAAACGI/E2q_aZ3mvk0/s1600/12.%E9%81%B8%E6%93%87%E8%B3%87%E6%96%99%E9%9B%86.png)](http://1.bp.blogspot.com/-LRgNR0Iac18/VKpRuk2t4mI/AAAAAAAACGI/E2q_aZ3mvk0/s1600/12.%E9%81%B8%E6%93%87%E8%B3%87%E6%96%99%E9%9B%86.png)</div>
資料來源就新增成功了，另外可以設定資料來源的讀取方式
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-dI5zYtWc3ek/VKpRu4kXJzI/AAAAAAAACGQ/o1w-jfPVudY/s1600/13.%E6%AA%94%E6%A1%88%E8%AE%80%E5%8F%96%E6%96%B9%E5%BC%8F.png)](http://1.bp.blogspot.com/-dI5zYtWc3ek/VKpRu4kXJzI/AAAAAAAACGQ/o1w-jfPVudY/s1600/13.%E6%AA%94%E6%A1%88%E8%AE%80%E5%8F%96%E6%96%B9%E5%BC%8F.png)</div>
在要繫結的項目上，直接選擇到要繫結的欄位就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-BhdUQ0pU1t0/VKpRvdVVaHI/AAAAAAAACGU/SA1NC1Mn5wg/s1600/14.%E7%B9%AB%E7%B5%90%E8%B3%87%E6%96%99.png)](http://2.bp.blogspot.com/-BhdUQ0pU1t0/VKpRvdVVaHI/AAAAAAAACGU/SA1NC1Mn5wg/s1600/14.%E7%B9%AB%E7%B5%90%E8%B3%87%E6%96%99.png)</div>
開始執行測試
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-n_xmXtdHKMw/VKpRv_19ZVI/AAAAAAAACGk/VdVv76xipmE/s1600/15.%E5%9F%B7%E8%A1%8C%E6%B8%AC%E8%A9%A6.png)](http://1.bp.blogspot.com/-n_xmXtdHKMw/VKpRv_19ZVI/AAAAAAAACGk/VdVv76xipmE/s1600/15.%E5%9F%B7%E8%A1%8C%E6%B8%AC%E8%A9%A6.png)</div>
測試結果