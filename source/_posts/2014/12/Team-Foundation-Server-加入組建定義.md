---
title: Team Foundation Server 加入組建定義
tags:
  - Team Foundation Server
date: 2014-12-31 19:06:00
---

打開Team Explorer，點擊組建
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-5pCfNH8CTkU/VKPYCjBRWoI/AAAAAAAACBc/7O1dWcBkRUw/s1600/01.%E5%8A%A0%E5%85%A5%E7%B5%84%E5%BB%BA.png)](http://2.bp.blogspot.com/-5pCfNH8CTkU/VKPYCjBRWoI/AAAAAAAACBc/7O1dWcBkRUw/s1600/01.%E5%8A%A0%E5%85%A5%E7%B5%84%E5%BB%BA.png)</div>
新增組建定義
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-6xrdwLtukgg/VKPYCukG-sI/AAAAAAAACBY/SpsW1Y3Q-Ok/s1600/02.%E6%96%B0%E5%A2%9E%E7%B5%84%E5%BB%BA%E5%AE%9A%E7%BE%A9.png)](http://4.bp.blogspot.com/-6xrdwLtukgg/VKPYCukG-sI/AAAAAAAACBY/SpsW1Y3Q-Ok/s1600/02.%E6%96%B0%E5%A2%9E%E7%B5%84%E5%BB%BA%E5%AE%9A%E7%BE%A9.png)</div>
組建定義名稱
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Bllqjy9lwNs/VKPYKJN42sI/AAAAAAAACCw/92afSzDahf4/s1600/03.%E7%B5%84%E5%BB%BA%E5%AE%9A%E7%BE%A9%E5%90%8D%E7%A8%B1.png)](http://2.bp.blogspot.com/-Bllqjy9lwNs/VKPYKJN42sI/AAAAAAAACCw/92afSzDahf4/s1600/03.%E7%B5%84%E5%BB%BA%E5%AE%9A%E7%BE%A9%E5%90%8D%E7%A8%B1.png)</div>
觸發程序用來設定何時執行這個建置
連續整合是每當程式碼簽入時就會觸發
累積簽入是設定至少多少時間才執行一次建置，用來避免頻繁簽入所造成的效能影響
閘道簽入是只有通過建置，才讓原始碼簽入，用來做建置條件的檢查
排程可以設定固定時間啟動建置
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-H5_6gnigVUU/VKPYDnW7MiI/AAAAAAAACBg/uRzajdqu5HI/s1600/04.%E8%A7%B8%E7%99%BC%E7%A8%8B%E5%BA%8F.png)](http://1.bp.blogspot.com/-H5_6gnigVUU/VKPYDnW7MiI/AAAAAAAACBg/uRzajdqu5HI/s1600/04.%E8%A7%B8%E7%99%BC%E7%A8%8B%E5%BA%8F.png)</div>
來源設定用來設定原始碼從何而來
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-JwHAof2PoZY/VKPYEfu1L9I/AAAAAAAACBk/8qwgBZ5COJg/s1600/05.%E4%BE%86%E6%BA%90%E8%A8%AD%E5%AE%9A.png)](http://4.bp.blogspot.com/-JwHAof2PoZY/VKPYEfu1L9I/AAAAAAAACBk/8qwgBZ5COJg/s1600/05.%E4%BE%86%E6%BA%90%E8%A8%AD%E5%AE%9A.png)</div>
組建預設值用來設定建置成功後的產品要輸出到什麼地方
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-tcu5d7h4QKc/VKPYEzSB7uI/AAAAAAAACBo/EADMiKvNxVs/s1600/06.%E7%B5%84%E5%BB%BA%E9%A0%90%E8%A8%AD%E5%80%BC.png)](http://1.bp.blogspot.com/-tcu5d7h4QKc/VKPYEzSB7uI/AAAAAAAACBo/EADMiKvNxVs/s1600/06.%E7%B5%84%E5%BB%BA%E9%A0%90%E8%A8%AD%E5%80%BC.png)</div>
流程是用來設定建置的動作和細部的設定
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-QFoV7prmOIQ/VKPYFU7ZCBI/AAAAAAAACBs/xlRpNrBS9Yk/s1600/07.%E6%B5%81%E7%A8%8B.png)](http://4.bp.blogspot.com/-QFoV7prmOIQ/VKPYFU7ZCBI/AAAAAAAACBs/xlRpNrBS9Yk/s1600/07.%E6%B5%81%E7%A8%8B.png)</div>
保留原則用來設定不同建置結果下是否要保留建置出來的產品
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-2OhX8zi3otQ/VKPYGMcgY1I/AAAAAAAACB0/UfuRSYk-VHs/s1600/08.%E4%BF%9D%E7%95%99%E5%8E%9F%E5%89%87.png)](http://4.bp.blogspot.com/-2OhX8zi3otQ/VKPYGMcgY1I/AAAAAAAACB0/UfuRSYk-VHs/s1600/08.%E4%BF%9D%E7%95%99%E5%8E%9F%E5%89%87.png)</div>
設定好後按存檔就行了，在組建定義中就可以看到剛建立的組建定義
在上面按右鍵，選擇佇列新組建，就可以手動執行這個組建定義
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-9eXfenIcV3s/VKPYGYsKPSI/AAAAAAAACB4/Y_peIkvWLOQ/s1600/09.%E4%BD%87%E5%88%97%E6%96%B0%E7%B5%84%E5%BB%BA.png)](http://3.bp.blogspot.com/-9eXfenIcV3s/VKPYGYsKPSI/AAAAAAAACB4/Y_peIkvWLOQ/s1600/09.%E4%BD%87%E5%88%97%E6%96%B0%E7%B5%84%E5%BB%BA.png)</div>
手動執行之前，可以設定一下這一次的組建的控制器和代理
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-gI0RbdwJnrI/VKPYG9_9PCI/AAAAAAAACB8/YyrgxRatotw/s1600/10.%E4%BD%87%E5%88%97%E8%A8%AD%E5%AE%9A.png)](http://3.bp.blogspot.com/-gI0RbdwJnrI/VKPYG9_9PCI/AAAAAAAACB8/YyrgxRatotw/s1600/10.%E4%BD%87%E5%88%97%E8%A8%AD%E5%AE%9A.png)</div>
雙擊組建定義，可以叫出組建記錄
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-KGGDERK0x_A/VKPYHUmTOiI/AAAAAAAACCE/7rYyXdOsQ-I/s1600/11.%E4%BD%87%E5%88%97%E9%A0%85%E7%9B%AE.png)](http://2.bp.blogspot.com/-KGGDERK0x_A/VKPYHUmTOiI/AAAAAAAACCE/7rYyXdOsQ-I/s1600/11.%E4%BD%87%E5%88%97%E9%A0%85%E7%9B%AE.png)</div>
雙擊組建記錄，可以看該次組建的結果
這次組建失敗，原因是少了Microsoft.WebApplication.targets
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-7sYEMorvllg/VKPYH1TqzQI/AAAAAAAACCM/OveXOPeJ93w/s1600/12.%2B%E5%BB%BA%E7%BD%AE%E8%A8%8A%E6%81%AF.png)](http://1.bp.blogspot.com/-7sYEMorvllg/VKPYH1TqzQI/AAAAAAAACCM/OveXOPeJ93w/s1600/12.%2B%E5%BB%BA%E7%BD%AE%E8%A8%8A%E6%81%AF.png)</div>
可以手動複製這個資料夾到組建伺服器上相同的位置
比較簡單的方式是安裝Visual Studio Shell轉散發套件
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-lOBgzNLC6Os/VKPYIbMM94I/AAAAAAAACCU/vYBfxTzTUhE/s1600/13.%E5%8A%A0%E5%85%A5Shell.png)](http://4.bp.blogspot.com/-lOBgzNLC6Os/VKPYIbMM94I/AAAAAAAACCU/vYBfxTzTUhE/s1600/13.%E5%8A%A0%E5%85%A5Shell.png)</div>
就會有相關的檔案了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-pzNYLUS1G9E/VKPYImLuIaI/AAAAAAAACCY/XbnEeEJgXak/s1600/14.%E5%8A%A0%E5%85%A5target.png)](http://3.bp.blogspot.com/-pzNYLUS1G9E/VKPYImLuIaI/AAAAAAAACCY/XbnEeEJgXak/s1600/14.%E5%8A%A0%E5%85%A5target.png)</div>
再執行一次就建置成功了
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-N_QbhlPGKS0/VKPYJYlpMGI/AAAAAAAACCo/uHMG_d0TXjk/s1600/15.%E5%BB%BA%E7%BD%AE%E6%88%90%E5%8A%9F.png)](http://4.bp.blogspot.com/-N_QbhlPGKS0/VKPYJYlpMGI/AAAAAAAACCo/uHMG_d0TXjk/s1600/15.%E5%BB%BA%E7%BD%AE%E6%88%90%E5%8A%9F.png)</div>