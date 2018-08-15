---
title: SQL Server 資料層應用程式
tags:
  - SQL Server
date: 2014-06-17 15:50:00
---

<div>為了方便練習，所以透過SQL LocalDB建立兩個執行個體</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-PYm-vP7F9SQ/U5_tXS5y79I/AAAAAAAABbY/QPu4WEiLHPY/s1600/01.%25E5%25BB%25BA%25E7%2592%25B0%25E5%25A2%2583.png)](http://1.bp.blogspot.com/-PYm-vP7F9SQ/U5_tXS5y79I/AAAAAAAABbY/QPu4WEiLHPY/s1600/01.%25E5%25BB%25BA%25E7%2592%25B0%25E5%25A2%2583.png)</div>
<div>再來建立一個練習用的資料庫，這裡用北風資料庫為例子</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-QazOoP4b4vU/U5_tXe_J0JI/AAAAAAAABbk/pq6cEvQRC8w/s1600/02.%25E5%258C%2597%25E9%25A2%25A8%25E8%25B3%2587%25E6%2596%2599%25E5%25BA%25AB.png)](http://4.bp.blogspot.com/-QazOoP4b4vU/U5_tXe_J0JI/AAAAAAAABbk/pq6cEvQRC8w/s1600/02.%25E5%258C%2597%25E9%25A2%25A8%25E8%25B3%2587%25E6%2596%2599%25E5%25BA%25AB.png)</div>
<div>首先把資料庫註冊成資料層應用程式</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-e0MTcSY8jTM/U5_tXfsjfyI/AAAAAAAABbw/Pufq3ukfQOQ/s1600/03.%25E8%25A8%25BB%25E5%2586%258A.png)](http://1.bp.blogspot.com/-e0MTcSY8jTM/U5_tXfsjfyI/AAAAAAAABbw/Pufq3ukfQOQ/s1600/03.%25E8%25A8%25BB%25E5%2586%258A.png)</div>
<div>設定屬性
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-Pl3r-mf7M_s/U5_tXxN09nI/AAAAAAAABbo/FdNbbjp1-P8/s1600/04.%25E8%25A8%25BB%25E5%2586%258A%25E5%25B1%25AC%25E6%2580%25A7.png)](http://1.bp.blogspot.com/-Pl3r-mf7M_s/U5_tXxN09nI/AAAAAAAABbo/FdNbbjp1-P8/s1600/04.%25E8%25A8%25BB%25E5%2586%258A%25E5%25B1%25AC%25E6%2580%25A7.png)</div>
驗證與摘要
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-c4VmOP54fdc/U5_tYMrk4pI/AAAAAAAABeY/uCabHv_R9SA/s1600/05.%25E8%25A8%25BB%25E5%2586%258A%25E6%2591%2598%25E8%25A6%2581.png)](http://4.bp.blogspot.com/-c4VmOP54fdc/U5_tYMrk4pI/AAAAAAAABeY/uCabHv_R9SA/s1600/05.%25E8%25A8%25BB%25E5%2586%258A%25E6%2591%2598%25E8%25A6%2581.png)</div>
註冊完成
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-VFcJVLC0KFU/U5_tYT_tj-I/AAAAAAAABb4/a8aRtT07uE4/s1600/06.%25E8%25A8%25BB%25E5%2586%258A%25E5%25AE%258C%25E6%2588%2590.png)](http://4.bp.blogspot.com/-VFcJVLC0KFU/U5_tYT_tj-I/AAAAAAAABb4/a8aRtT07uE4/s1600/06.%25E8%25A8%25BB%25E5%2586%258A%25E5%25AE%258C%25E6%2588%2590.png)</div>
再來擷取資料層應用程式，不用註冊也可以直接擷取</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-RSIBOQZNGCM/U5_tY546YjI/AAAAAAAABec/W0PK5ycOF_k/s1600/07.%25E6%2593%25B7%25E5%258F%2596.png)](http://1.bp.blogspot.com/-RSIBOQZNGCM/U5_tY546YjI/AAAAAAAABec/W0PK5ycOF_k/s1600/07.%25E6%2593%25B7%25E5%258F%2596.png)</div>
<div>選擇檔案輸出的路徑和檔名
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-LLMbv0HkHOE/U5_tZNY6SaI/AAAAAAAABcM/spVOVImkRGk/s1600/08.%25E6%2593%25B7%25E5%258F%2596%25E5%25B1%25AC%25E6%2580%25A7.png)](http://3.bp.blogspot.com/-LLMbv0HkHOE/U5_tZNY6SaI/AAAAAAAABcM/spVOVImkRGk/s1600/08.%25E6%2593%25B7%25E5%258F%2596%25E5%25B1%25AC%25E6%2580%25A7.png)</div>
驗證與摘要
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-61wr623zbFM/U5_tZRMNqLI/AAAAAAAABcU/WeBsHrL7iwY/s1600/09.%25E6%2593%25B7%25E5%258F%2596%25E6%2591%2598%25E8%25A6%2581.png)](http://4.bp.blogspot.com/-61wr623zbFM/U5_tZRMNqLI/AAAAAAAABcU/WeBsHrL7iwY/s1600/09.%25E6%2593%25B7%25E5%258F%2596%25E6%2591%2598%25E8%25A6%2581.png)</div>
封裝完成
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-cLyszCK0cvA/U5_tZ8t6XyI/AAAAAAAABck/OAtx5RDGruQ/s1600/10.%25E6%2593%25B7%25E5%258F%2596%25E5%25AE%258C%25E6%2588%2590.png)](http://4.bp.blogspot.com/-cLyszCK0cvA/U5_tZ8t6XyI/AAAAAAAABck/OAtx5RDGruQ/s1600/10.%25E6%2593%25B7%25E5%258F%2596%25E5%25AE%258C%25E6%2588%2590.png)</div>
再來把擷取出來的檔案部署到第二個環境</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-HW0bgK0INAE/U5_taIk8hfI/AAAAAAAABeI/MdQ6LrTAvcc/s1600/11.%25E9%2583%25A8%25E7%25BD%25B2.png)](http://4.bp.blogspot.com/-HW0bgK0INAE/U5_taIk8hfI/AAAAAAAABeI/MdQ6LrTAvcc/s1600/11.%25E9%2583%25A8%25E7%25BD%25B2.png)</div>
<div>選擇剛輸出的檔案
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-hD5cEqITLcM/U5_taFULOqI/AAAAAAAABcg/mxhSAzjH0wA/s1600/12.%25E9%2583%25A8%25E6%259A%2591%25E9%2581%25B8%25E6%25AA%2594.png)](http://4.bp.blogspot.com/-hD5cEqITLcM/U5_taFULOqI/AAAAAAAABcg/mxhSAzjH0wA/s1600/12.%25E9%2583%25A8%25E6%259A%2591%25E9%2581%25B8%25E6%25AA%2594.png)</div>
設定要部署的資料庫名稱
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/--HEJU57mtNU/U5_taRjuiiI/AAAAAAAABc0/u6ZaFtAdBiA/s1600/13.%25E9%2583%25A8%25E7%25BD%25B2%25E5%2590%258D%25E7%25A8%25B1.png)](http://3.bp.blogspot.com/--HEJU57mtNU/U5_taRjuiiI/AAAAAAAABc0/u6ZaFtAdBiA/s1600/13.%25E9%2583%25A8%25E7%25BD%25B2%25E5%2590%258D%25E7%25A8%25B1.png)</div>
部署摘要
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-kAAdV8Uf_WE/U5_tazOwtdI/AAAAAAAABco/st3V2Dhj1zk/s1600/14.%25E9%2583%25A8%25E7%25BD%25B2%25E6%2591%2598%25E8%25A6%2581.png)](http://3.bp.blogspot.com/-kAAdV8Uf_WE/U5_tazOwtdI/AAAAAAAABco/st3V2Dhj1zk/s1600/14.%25E9%2583%25A8%25E7%25BD%25B2%25E6%2591%2598%25E8%25A6%2581.png)</div>
部署完成
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-h_FTGXGLzVA/U5_tbOrYbXI/AAAAAAAABc8/0bFQzE8Av30/s1600/15.%25E9%2583%25A8%25E7%25BD%25B2%25E5%25AE%258C%25E6%2588%2590.png)](http://4.bp.blogspot.com/-h_FTGXGLzVA/U5_tbOrYbXI/AAAAAAAABc8/0bFQzE8Av30/s1600/15.%25E9%2583%25A8%25E7%25BD%25B2%25E5%25AE%258C%25E6%2588%2590.png)</div>
第二個環境也有北風資料庫了
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-KhTDtavtW30/U5_tbfNVwCI/AAAAAAAABeQ/RIxgYNMd3z8/s1600/16.%25E9%2583%25A8%25E7%25BD%25B2%25E5%25BE%258C%25E7%259A%2584%25E6%25A8%25A3%25E5%25AD%2590.png)](http://2.bp.blogspot.com/-KhTDtavtW30/U5_tbfNVwCI/AAAAAAAABeQ/RIxgYNMd3z8/s1600/16.%25E9%2583%25A8%25E7%25BD%25B2%25E5%25BE%258C%25E7%259A%2584%25E6%25A8%25A3%25E5%25AD%2590.png)</div>
再來異動第一個環境的資料庫的schema，這裡用新增一個資料表當例子
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Z9Ah5th7ysI/U5_tcFWAAFI/AAAAAAAABdI/9CNike4If7w/s1600/17.%25E6%2596%25B0%25E5%25A2%259E%25E8%25B3%2587%25E6%2596%2599%25E8%25A1%25A8.png)](http://4.bp.blogspot.com/-Z9Ah5th7ysI/U5_tcFWAAFI/AAAAAAAABdI/9CNike4If7w/s1600/17.%25E6%2596%25B0%25E5%25A2%259E%25E8%25B3%2587%25E6%2596%2599%25E8%25A1%25A8.png)</div>
</div>再擷取一次資料層應用程式
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-aefoQHvcJwA/U5_tcsH9hwI/AAAAAAAABdc/kYcdxZRIwEg/s1600/18-1.%25E5%2586%258D%25E6%2593%25B7%25E5%258F%2596%25E4%25B8%2580%25E6%25AC%25A1.png)](http://2.bp.blogspot.com/-aefoQHvcJwA/U5_tcsH9hwI/AAAAAAAABdc/kYcdxZRIwEg/s1600/18-1.%25E5%2586%258D%25E6%2593%25B7%25E5%258F%2596%25E4%25B8%2580%25E6%25AC%25A1.png)</div>
在第二個環境上用升級的方式匯入
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-fmVxwKzU1Zk/U5_tcqyqHTI/AAAAAAAABdU/xYCAJbOrZVw/s1600/18-2.%25E5%258D%2587%25E7%25B4%259A.png)](http://3.bp.blogspot.com/-fmVxwKzU1Zk/U5_tcqyqHTI/AAAAAAAABdU/xYCAJbOrZVw/s1600/18-2.%25E5%258D%2587%25E7%25B4%259A.png)</div>
<div>選擇剛匯出的檔案
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-0dr008Hag30/U5_tdDzNlDI/AAAAAAAABeU/QFWzbi0JWZY/s1600/19.%25E5%258D%2587%25E7%25B4%259A%25E9%2581%25B8%25E6%25AA%2594.png)](http://1.bp.blogspot.com/-0dr008Hag30/U5_tdDzNlDI/AAAAAAAABeU/QFWzbi0JWZY/s1600/19.%25E5%258D%2587%25E7%25B4%259A%25E9%2581%25B8%25E6%25AA%2594.png)</div>
</div>這邊的尚未變更指的是從上次建立資料層應用程式後都沒有變更Schema
而不是和要升級的檔案比對的結果
<div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-u0kKhoucR7Q/U5_tdQeE3MI/AAAAAAAABeA/IRpxqd8w-Z4/s1600/20.%25E5%258D%2587%25E7%25B4%259A%25E5%2581%25B5%25E6%25B8%25AC%25E7%25B5%2590%25E6%259E%259C.png)](http://3.bp.blogspot.com/-u0kKhoucR7Q/U5_tdQeE3MI/AAAAAAAABeA/IRpxqd8w-Z4/s1600/20.%25E5%258D%2587%25E7%25B4%259A%25E5%2581%25B5%25E6%25B8%25AC%25E7%25B5%2590%25E6%259E%259C.png)</div>
</div>升級選項
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-WZ8HUXKankM/U5_tdzT3F1I/AAAAAAAABdo/Vldgx3uqvPs/s1600/21.%25E5%258D%2587%25E7%25B4%259A%25E9%2581%25B8%25E9%25A0%2585.png)](http://1.bp.blogspot.com/-WZ8HUXKankM/U5_tdzT3F1I/AAAAAAAABdo/Vldgx3uqvPs/s1600/21.%25E5%258D%2587%25E7%25B4%259A%25E9%2581%25B8%25E9%25A0%2585.png)</div>
<div>升級計畫</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-BDKkSYVWaHE/U5_td354TOI/AAAAAAAABd8/54GfkmMNWwU/s1600/22.%25E5%258D%2587%25E7%25B4%259A%25E8%25A8%2588%25E5%258A%2583.png)](http://4.bp.blogspot.com/-BDKkSYVWaHE/U5_td354TOI/AAAAAAAABd8/54GfkmMNWwU/s1600/22.%25E5%258D%2587%25E7%25B4%259A%25E8%25A8%2588%25E5%258A%2583.png)</div>
<div>升級摘要
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Mw0clAb-f5Q/U5_teYqP2zI/AAAAAAAABd0/Gwo6zt5Tr2c/s1600/23.%25E5%258D%2587%25E7%25B4%259A%25E6%2591%2598%25E8%25A6%2581.png)](http://4.bp.blogspot.com/-Mw0clAb-f5Q/U5_teYqP2zI/AAAAAAAABd0/Gwo6zt5Tr2c/s1600/23.%25E5%258D%2587%25E7%25B4%259A%25E6%2591%2598%25E8%25A6%2581.png)</div>
</div>升級完成
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-IE5yhPETFqQ/U5_telmV4VI/AAAAAAAABd4/Lse01AvDSkQ/s1600/24.%25E5%258D%2587%25E7%25B4%259A%25E5%25AE%258C%25E6%2588%2590.png)](http://3.bp.blogspot.com/-IE5yhPETFqQ/U5_telmV4VI/AAAAAAAABd4/Lse01AvDSkQ/s1600/24.%25E5%258D%2587%25E7%25B4%259A%25E5%25AE%258C%25E6%2588%2590.png)</div>
升級後可以看到新增的資料表
<div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-va77B4s-mHI/U5_te15PgUI/AAAAAAAABeM/Wp1USWOjwS4/s1600/25.%25E5%258D%2587%25E7%25B4%259A%25E5%25BE%258C%25E7%259A%2584%25E6%25A8%25A3%25E5%25AD%2590.png)](http://4.bp.blogspot.com/-va77B4s-mHI/U5_te15PgUI/AAAAAAAABeM/Wp1USWOjwS4/s1600/25.%25E5%258D%2587%25E7%25B4%259A%25E5%25BE%258C%25E7%259A%2584%25E6%25A8%25A3%25E5%25AD%2590.png)</div>
</div>