---
title: TeamCity 整合 StyleCop
tags:
  - StyleCop
  - TeamCity
date: 2014-06-06 14:10:00
---

先打開管理頁面的Plugin List，選擇[Available Plugin](http://confluence.jetbrains.com/display/TW/TeamCity+Plugins)
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-oDy7ga_ahsU/U5FaL4uSbTI/AAAAAAAABbI/bTAKqhJ56MQ/s1600/00.AvailablePlugin.png)](http://3.bp.blogspot.com/-oDy7ga_ahsU/U5FaL4uSbTI/AAAAAAAABbI/bTAKqhJ56MQ/s1600/00.AvailablePlugin.png)</div>
找到StyleCop Runner
<div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Y0Omog127jg/U5FUq4nBNBI/AAAAAAAABZU/zO4XKx93Lxs/s1600/01.Download.png)](http://4.bp.blogspot.com/-Y0Omog127jg/U5FUq4nBNBI/AAAAAAAABZU/zO4XKx93Lxs/s1600/01.Download.png)</div>
</div><div>下載最新版本的StyleCop Plugin
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-ivWisnEKuWc/U5FUvySNMtI/AAAAAAAABZc/aQ4RiKU-5Bo/s1600/02.DW.png)](http://4.bp.blogspot.com/-ivWisnEKuWc/U5FUvySNMtI/AAAAAAAABZc/aQ4RiKU-5Bo/s1600/02.DW.png)</div>
</div><div>
</div><div>把檔案解壓縮後會得到不帶版本號的Stylecop.zip
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-3HndiN2ipLY/U5FU5j_9pvI/AAAAAAAABZk/01PnJvAMqqc/s1600/03.%E8%A7%A3%E5%A3%93%E7%B8%AE.png)](http://4.bp.blogspot.com/-3HndiN2ipLY/U5FU5j_9pvI/AAAAAAAABZk/01PnJvAMqqc/s1600/03.%E8%A7%A3%E5%A3%93%E7%B8%AE.png)</div>
</div><div>
打開管理頁面的PluginList，點擊Upload plugin zip連結</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-ZjTZdgwWpyc/U5FVDXCQCwI/AAAAAAAABZs/oZOweJhsvoU/s1600/04.PluginList.png)](http://4.bp.blogspot.com/-ZjTZdgwWpyc/U5FVDXCQCwI/AAAAAAAABZs/oZOweJhsvoU/s1600/04.PluginList.png)</div>
</div><div>選擇剛解壓縮出來的Stylecop.zip
上傳到Plugins資料夾下面</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-fMJo2RjNF1U/U5FVbVB5FEI/AAAAAAAABZ0/83_2pD59O64/s1600/05.Upload.png)](http://2.bp.blogspot.com/-fMJo2RjNF1U/U5FVbVB5FEI/AAAAAAAABZ0/83_2pD59O64/s1600/05.Upload.png)</div>
</div><div>重新啟動TeamCity服務</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-3pEb8Sw8AXs/U5FVrYnQCEI/AAAAAAAABZ8/EY91_ySL0WI/s1600/06.Restart.png)](http://4.bp.blogspot.com/-3pEb8Sw8AXs/U5FVrYnQCEI/AAAAAAAABZ8/EY91_ySL0WI/s1600/06.Restart.png)</div>
</div><div>Plugin列表中可以看到StyleCop套件的資訊</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-4boCfNRDupM/U5FVwJcK6xI/AAAAAAAABaE/NBUmGkfZgeI/s1600/07.AvailablePlugin.png)](http://2.bp.blogspot.com/-4boCfNRDupM/U5FVwJcK6xI/AAAAAAAABaE/NBUmGkfZgeI/s1600/07.AvailablePlugin.png)</div>
</div><div>Build Step中就可以選擇StyleCop這個Runner
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-avk9twecrxM/U5FWpaYUPoI/AAAAAAAABaQ/88_LXNHQWGE/s1600/08.BuildStep.png)](http://1.bp.blogspot.com/-avk9twecrxM/U5FWpaYUPoI/AAAAAAAABaQ/88_LXNHQWGE/s1600/08.BuildStep.png)</div>輸入選擇要檢查的檔案路徑和StyleCop.dll的路徑</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Ei7SIMcLMug/U5FXaI7eU0I/AAAAAAAABaY/ony7YCKBOg4/s1600/09.Setting.png)](http://3.bp.blogspot.com/-Ei7SIMcLMug/U5FXaI7eU0I/AAAAAAAABaY/ony7YCKBOg4/s1600/09.Setting.png)</div>
預設會把找到的問題當做錯誤，造成建置失敗
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Dt_BfUwJBrY/U5FYOQXn35I/AAAAAAAABak/sLzXeq4qBFc/s1600/10.Error.png)](http://4.bp.blogspot.com/-Dt_BfUwJBrY/U5FYOQXn35I/AAAAAAAABak/sLzXeq4qBFc/s1600/10.Error.png)</div>
可以修改Max Viloations，這是最大問題數的數量，超過就失敗，負數為不限制
另一個方法是勾選Treat errors as warnings，把錯誤當成警告
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-kcKgpBM4Egw/U5FYUjd0VXI/AAAAAAAABas/REIcyjgbnoo/s1600/11.Warn.png)](http://4.bp.blogspot.com/-kcKgpBM4Egw/U5FYUjd0VXI/AAAAAAAABas/REIcyjgbnoo/s1600/11.Warn.png)</div>
建置結果會順利通過，但有檢查到的數量顯示
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-pR918wQlwpo/U5FYc5uSooI/AAAAAAAABa0/fL2NrOd53uQ/s1600/12.Warb.png)](http://4.bp.blogspot.com/-pR918wQlwpo/U5FYc5uSooI/AAAAAAAABa0/fL2NrOd53uQ/s1600/12.Warb.png)</div>
點選該筆建置內容，就會看到StyleCop的詳細資料
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-NyrSWvNkOE0/U5FYgh8O-hI/AAAAAAAABa8/tpdrcCrEjww/s1600/13.Detail.png)](http://2.bp.blogspot.com/-NyrSWvNkOE0/U5FYgh8O-hI/AAAAAAAABa8/tpdrcCrEjww/s1600/13.Detail.png)</div>

</div><div>
</div>