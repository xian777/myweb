---
title: Visual Studio 新增擴充套件
tags:
  - visual studio
date: 2014-04-09 16:29:00
---

建立好專案和項目範本後，雖然只是放到固定的資料夾就可以使用
但如果要和團隊分享的話，可以考慮新增一個擴充套件比較方便

首先要先安裝Visual Studio SKD，這裡以2013版為例
[http://www.microsoft.com/en-us/download/details.aspx?id=40758](http://www.microsoft.com/en-us/download/details.aspx?id=40758)
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-FbinvEcsJ2g/U0UDS0sHgVI/AAAAAAAABMg/VISEcc-iCQw/s1600/01.%E4%B8%8B%E8%BC%89SDK.png)](http://4.bp.blogspot.com/-FbinvEcsJ2g/U0UDS0sHgVI/AAAAAAAABMg/VISEcc-iCQw/s1600/01.%E4%B8%8B%E8%BC%89SDK.png)</div>

安裝後開新專案在擴充性下面就會有一個VSIX專案
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Zp6MpLRTQLA/U0UDXn5GLsI/AAAAAAAABM0/IDSfh9A30CQ/s1600/02.%25E6%2596%25B0%25E5%25A2%259E%25E6%2593%25B4%25E5%2585%2585%25E5%25B0%2588%25E6%25A1%2588.png)](http://2.bp.blogspot.com/-Zp6MpLRTQLA/U0UDXn5GLsI/AAAAAAAABM0/IDSfh9A30CQ/s1600/02.%25E6%2596%25B0%25E5%25A2%259E%25E6%2593%25B4%25E5%2585%2585%25E5%25B0%2588%25E6%25A1%2588.png)</div>
先把專案資訊填一填
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-z3eh5_sZQWY/U0UDXk8A3EI/AAAAAAAABM4/Ljf-XvB7oAg/s1600/03.%25E5%25B0%2588%25E6%25A1%2588%25E8%25B3%2587%25E8%25A8%258A.png)](http://3.bp.blogspot.com/-z3eh5_sZQWY/U0UDXk8A3EI/AAAAAAAABM4/Ljf-XvB7oAg/s1600/03.%25E5%25B0%2588%25E6%25A1%2588%25E8%25B3%2587%25E8%25A8%258A.png)</div>
這邊是選擇可以安裝這個擴充套件的Visual Studio版本
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Y5sSIH4G_fE/U0UDXo4clOI/AAAAAAAABM8/8KDpA-9sg0s/s1600/04.%25E5%25AE%2589%25E8%25A3%259D%25E7%259B%25AE%25E6%25A8%2599.png)](http://2.bp.blogspot.com/-Y5sSIH4G_fE/U0UDXo4clOI/AAAAAAAABM8/8KDpA-9sg0s/s1600/04.%25E5%25AE%2589%25E8%25A3%259D%25E7%259B%25AE%25E6%25A8%2599.png)</div>
這邊是選擇要安裝的項目，也是主要設定的項目
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-VDQLbbUkRtU/U0UDarsXt5I/AAAAAAAABNs/Nk_mPTKtGa4/s1600/05.%25E8%25A6%2581%25E5%25AE%2589%25E8%25A3%259D%25E7%259A%2584%25E9%25A0%2585%25E7%259B%25AE.png)](http://2.bp.blogspot.com/-VDQLbbUkRtU/U0UDarsXt5I/AAAAAAAABNs/Nk_mPTKtGa4/s1600/05.%25E8%25A6%2581%25E5%25AE%2589%25E8%25A3%259D%25E7%259A%2584%25E9%25A0%2585%25E7%259B%25AE.png)</div>
先新增一個專案範本，選擇之前建立的範本
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-5WT7V3S0ZDQ/U0UDYZ4msII/AAAAAAAABNQ/uq8y3BuqMc0/s1600/06.%25E6%2596%25B0%25E5%25A2%259E%25E5%25B0%2588%25E6%25A1%2588%25E7%25AF%2584%25E6%259C%25AC.png)](http://1.bp.blogspot.com/-5WT7V3S0ZDQ/U0UDYZ4msII/AAAAAAAABNQ/uq8y3BuqMc0/s1600/06.%25E6%2596%25B0%25E5%25A2%259E%25E5%25B0%2588%25E6%25A1%2588%25E7%25AF%2584%25E6%259C%25AC.png)</div>
再新增一個項目範本，選擇之前建立的範本
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-z1Y2u-EpCCM/U0UDYvmMuMI/AAAAAAAABNI/320yJqFRKXQ/s1600/07.%25E6%2596%25B0%25E5%25A2%259E%25E9%25A0%2585%25E7%259B%25AE%25E7%25AF%2584%25E6%259C%25AC.png)](http://1.bp.blogspot.com/-z1Y2u-EpCCM/U0UDYvmMuMI/AAAAAAAABNI/320yJqFRKXQ/s1600/07.%25E6%2596%25B0%25E5%25A2%259E%25E9%25A0%2585%25E7%259B%25AE%25E7%25AF%2584%25E6%259C%25AC.png)</div>
設定好後會自動把範本複製進來，基本這樣就完成了
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-9GvJmdfXOS0/U0UDZZXbXRI/AAAAAAAABNY/-wf7K2t_dsE/s1600/08.%25E7%25AF%2584%25E6%259C%25AC%25E8%25B7%25AF%25E5%25BE%2591.png)](http://4.bp.blogspot.com/-9GvJmdfXOS0/U0UDZZXbXRI/AAAAAAAABNY/-wf7K2t_dsE/s1600/08.%25E7%25AF%2584%25E6%259C%25AC%25E8%25B7%25AF%25E5%25BE%2591.png)</div>

但是範本會和預設的範本混在一起，為了方便起來還是建立一個自訂的分類比較好找
所以手動調整一下，新增一個資料夾就行了，資料夾名稱就要自訂分類的名稱
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-lSdbxhJb020/U0UDZhk7jXI/AAAAAAAABNg/MX0pMyUpVJk/s1600/09.%25E8%25AA%25BF%25E6%2595%25B4%25E5%25BE%258C%25E7%259A%2584%25E8%25B7%25AF%25E5%25BE%2591.png)](http://2.bp.blogspot.com/-lSdbxhJb020/U0UDZhk7jXI/AAAAAAAABNg/MX0pMyUpVJk/s1600/09.%25E8%25AA%25BF%25E6%2595%25B4%25E5%25BE%258C%25E7%259A%2584%25E8%25B7%25AF%25E5%25BE%2591.png)</div>
設定好了建置一下方案，就可以得到這個擴充套件了
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-IifBLJWGli8/U0UEfzUfRwI/AAAAAAAABN0/21BH5AY8meo/s1600/10.%E5%BB%BA%E7%BD%AE.png)](http://4.bp.blogspot.com/-IifBLJWGli8/U0UEfzUfRwI/AAAAAAAABN0/21BH5AY8meo/s1600/10.%E5%BB%BA%E7%BD%AE.png)</div>
延伸閱讀

[新增專案範本](https://www.blogger.com/goog_1441465550)
[http://blog.developer.idv.tw/2014/04/visual-studio.html](http://blog.developer.idv.tw/2014/04/visual-studio.html)

[新增項目範本](https://www.blogger.com/goog_1441465555)
[http://blog.developer.idv.tw/2014/04/visual-studio_9.html](http://blog.developer.idv.tw/2014/04/visual-studio_9.html)

參考連結
[http://timheuer.com/blog/archive/2010/05/03/create-vsix-files-with-visual-studio-template-deployment.aspx](http://timheuer.com/blog/archive/2010/05/03/create-vsix-files-with-visual-studio-template-deployment.aspx)

[http://msdn.microsoft.com/zh-tw/library/ms247119.aspx](http://msdn.microsoft.com/zh-tw/library/ms247119.aspx)