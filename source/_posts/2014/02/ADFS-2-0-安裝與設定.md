---
title: ADFS 2.0 安裝與設定
tags:
  - ADFS
  - Claims Base
  - SSO
date: 2014-02-14 10:37:00
---

Windows 2008 Server內建的ADFS是1.0版，要安裝2.0版需要手動[下載安裝](http://www.microsoft.com/zh-tw/download/details.aspx?id=10909)
安裝的過程還滿簡單的，只有幾個設定而已，開始下一步吧

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-8oaOTcFeeUM/Uv153SrSAJI/AAAAAAAABAI/_xcSqiyUb78/s1600/01.png)](http://2.bp.blogspot.com/-8oaOTcFeeUM/Uv153SrSAJI/AAAAAAAABAI/_xcSqiyUb78/s1600/01.png)</div>
同意授權合約才可繼續下一步
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-zfdsDgP6C_o/Uv155lilVpI/AAAAAAAABAg/K6MXCm1D1vY/s1600/02.png)](http://3.bp.blogspot.com/-zfdsDgP6C_o/Uv155lilVpI/AAAAAAAABAg/K6MXCm1D1vY/s1600/02.png)</div>
這裡以安裝同盟伺服器為例子
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-TPgO9T-t-rQ/Uv155nOki4I/AAAAAAAABAc/pdUeIXJ0-4k/s1600/03.png)](http://2.bp.blogspot.com/-TPgO9T-t-rQ/Uv155nOki4I/AAAAAAAABAc/pdUeIXJ0-4k/s1600/03.png)</div>
安裝的先決條件軟體，需要一點時間
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-9ABxhIV9Vrk/Uv155hp8kwI/AAAAAAAABAk/KoOfO_MZEqk/s1600/04.png)](http://3.bp.blogspot.com/-9ABxhIV9Vrk/Uv155hp8kwI/AAAAAAAABAk/KoOfO_MZEqk/s1600/04.png)</div>
安裝好了
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Ja5YY_KbBjo/Uv16-xCBwPI/AAAAAAAABAs/j8g0Pt4u-ro/s1600/05.png)](http://2.bp.blogspot.com/-Ja5YY_KbBjo/Uv16-xCBwPI/AAAAAAAABAs/j8g0Pt4u-ro/s1600/05.png)</div>
先來設定同盟伺服器
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-B-lvhmoco5Q/Uv17Q77tGcI/AAAAAAAABA0/m4Km-nc3HFo/s1600/06.png)](http://4.bp.blogspot.com/-B-lvhmoco5Q/Uv17Q77tGcI/AAAAAAAABA0/m4Km-nc3HFo/s1600/06.png)</div>
建立一個新的Federation Server
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Hb97KqSKg6g/Uv17sparJoI/AAAAAAAABBA/IkZrSc_m_-8/s1600/07.png)](http://2.bp.blogspot.com/-Hb97KqSKg6g/Uv17sparJoI/AAAAAAAABBA/IkZrSc_m_-8/s1600/07.png)</div>
選擇獨立同盟伺服器
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-BAPk5nzxTqA/Uv17suHq9_I/AAAAAAAABBE/akZowV4m6HA/s1600/08.png)](http://1.bp.blogspot.com/-BAPk5nzxTqA/Uv17suHq9_I/AAAAAAAABBE/akZowV4m6HA/s1600/08.png)</div>
這裡需要SSL憑證，要測試的話可以先用本機簽署一個
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-MIrq5V6eH6U/Uv17uHJvnfI/AAAAAAAABBQ/xLL6V9qs770/s1600/09.png)](http://1.bp.blogspot.com/-MIrq5V6eH6U/Uv17uHJvnfI/AAAAAAAABBQ/xLL6V9qs770/s1600/09.png)</div>
先打開IIS選擇伺服器憑證
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-QKFxIEJEwxE/Uv1_alnCAxI/AAAAAAAABBk/TiPelyRZmqM/s1600/09-1.png)](http://2.bp.blogspot.com/-QKFxIEJEwxE/Uv1_alnCAxI/AAAAAAAABBk/TiPelyRZmqM/s1600/09-1.png)</div>
建立自我簽署憑證
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Go2cqtUcxPo/Uv1_alfZIMI/AAAAAAAABBs/J0A94Qjv784/s1600/09-2.png)](http://4.bp.blogspot.com/-Go2cqtUcxPo/Uv1_alfZIMI/AAAAAAAABBs/J0A94Qjv784/s1600/09-2.png)</div>
輸入一個好記的名稱
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-dtCY5ofn_3o/Uv1_aqVRRuI/AAAAAAAABBc/vV5fSUYDcwo/s1600/09-3.png)](http://2.bp.blogspot.com/-dtCY5ofn_3o/Uv1_aqVRRuI/AAAAAAAABBc/vV5fSUYDcwo/s1600/09-3.png)</div>
建立完成
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-M97EKTrKQd8/Uv2CFsOglHI/AAAAAAAABCo/Qj5mN4mE6f0/s1600/10.png)](http://1.bp.blogspot.com/-M97EKTrKQd8/Uv2CFsOglHI/AAAAAAAABCo/Qj5mN4mE6f0/s1600/10.png)</div>
回來ADFS的設定畫面，應該可以看到剛建立的憑證
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-rSNULMrzuOU/Uv2CFqQfTlI/AAAAAAAABCk/gRApUbBZgvY/s1600/11.png)](http://1.bp.blogspot.com/-rSNULMrzuOU/Uv2CFqQfTlI/AAAAAAAABCk/gRApUbBZgvY/s1600/11.png)</div>
準備完成
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-q4ony3w5zK4/Uv1_cII8q4I/AAAAAAAABCI/w-Xw_27Yudg/s1600/12.png)](http://2.bp.blogspot.com/-q4ony3w5zK4/Uv1_cII8q4I/AAAAAAAABCI/w-Xw_27Yudg/s1600/12.png)</div>
接下來就讓安裝精靈跑一會吧
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-p9arEluH2uQ/Uv1_cFRVsyI/AAAAAAAABCM/_Gorjg0QsB8/s1600/13.png)](http://2.bp.blogspot.com/-p9arEluH2uQ/Uv1_cFRVsyI/AAAAAAAABCM/_Gorjg0QsB8/s1600/13.png)</div>
到此安裝完成
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-efC9QS5J9_s/Uv2BV0UXV5I/AAAAAAAABCU/QS7l1mMvhtw/s1600/14.png)](http://1.bp.blogspot.com/-efC9QS5J9_s/Uv2BV0UXV5I/AAAAAAAABCU/QS7l1mMvhtw/s1600/14.png)</div>