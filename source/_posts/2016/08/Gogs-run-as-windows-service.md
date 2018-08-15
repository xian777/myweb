---
title: Gogs run as windows service
tags:
  - gogs
date: 2016-08-14 16:21:00
---

在[官網的說明文件](https://gogs.io/docs/installation/run_as_windows_service)中有很詳細的介紹，記錄一下設定的方式
<div class="separator" style="clear: both; text-align: center;"></div>
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-zukzoZW1jNw/V7AoqLHfc5I/AAAAAAAAD10/M1QecGVWQz8rGHyY5U27Ej3KE61TVFtxwCLcB/s1600/01.png)](https://2.bp.blogspot.com/-zukzoZW1jNw/V7AoqLHfc5I/AAAAAAAAD10/M1QecGVWQz8rGHyY5U27Ej3KE61TVFtxwCLcB/s1600/01.png)</div><div class="separator" style="clear: both; text-align: center;"></div>
要注意的是設定檔的位置
一開始透過網頁初始化的時後，會新增一個自定義的設定文件在custom/conf/app.ini
但是gogs預設的設定檔位置則是在conf/app.ini，已經編譯在二進位檔裡面了
之後升級的時後才不會覆蓋掉自定義的設定
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-l7J3l9ssUNU/V7AoqD-4MhI/AAAAAAAAD14/eQKBYVgrziUFDkkR7832drzz2AlWWfejwCLcB/s1600/02.png)](https://4.bp.blogspot.com/-l7J3l9ssUNU/V7AoqD-4MhI/AAAAAAAAD14/eQKBYVgrziUFDkkR7832drzz2AlWWfejwCLcB/s1600/02.png)</div>
所以在註冊服務的時後，設定檔路徑要使用自定義的設定檔
打開命令列工具，透過sc命令新增一個服務
$sc create gogs start= auto binPath= ""D:\gogs\gogs.exe" web --config "D:\gogs\custom\conf\app.ini""
再透過net命令啟動服務
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-nc36vEiq4r0/V7AoqMA5idI/AAAAAAAAD1w/mveYHwW6ris0kQ70u6frrYcPyVKIk_IrwCLcB/s1600/03.png)](https://2.bp.blogspot.com/-nc36vEiq4r0/V7AoqMA5idI/AAAAAAAAD1w/mveYHwW6ris0kQ70u6frrYcPyVKIk_IrwCLcB/s1600/03.png)</div>
gogs服務已啟動
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-WhxSujJgC_Y/V7AoqniCSmI/AAAAAAAAD18/DadvnNTSKZY9BAc_sWButuYQl0D2W_OgACLcB/s1600/04.png)](https://1.bp.blogspot.com/-WhxSujJgC_Y/V7AoqniCSmI/AAAAAAAAD18/DadvnNTSKZY9BAc_sWButuYQl0D2W_OgACLcB/s1600/04.png)</div>