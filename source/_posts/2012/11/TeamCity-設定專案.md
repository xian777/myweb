---
title: TeamCity 設定專案
tags:
  - TeamCity
date: 2012-11-13 20:50:00
---

## 接下來開始設定專案，首先建立一個專案
![](http://2.bp.blogspot.com/-6Z--lc4grZs/UKI-cBf9wrI/AAAAAAAAAZQ/IxPCZASp194/s1600/01.DefaultPage.png)](http://2.bp.blogspot.com/-6Z--lc4grZs/UKI-cBf9wrI/AAAAAAAAAZQ/IxPCZASp194/s1600/01.DefaultPage.png)

## 輸入專案名稱和說明後，按下Create就行了
![](http://2.bp.blogspot.com/-RZqV75lOXLw/UKI-c1lNXgI/AAAAAAAAAZY/xBnae98EbRs/s1600/02.CreateProject.png)](http://2.bp.blogspot.com/-RZqV75lOXLw/UKI-c1lNXgI/AAAAAAAAAZY/xBnae98EbRs/s1600/02.CreateProject.png)

## 接下來要開始設定Build Configuration，免費版只能建20個
![](http://3.bp.blogspot.com/-cgPFA7QHV_Q/UKI-dRMINHI/AAAAAAAAAZg/_HNZLVsbKBY/s1600/03.CreateProjectSuccess.png)](http://3.bp.blogspot.com/-cgPFA7QHV_Q/UKI-dRMINHI/AAAAAAAAAZg/_HNZLVsbKBY/s1600/03.CreateProjectSuccess.png)

## 第一步是設定一個名稱，這裡以Release Build為例
Build number format是自動版號的格式，除了每次建置會自動加1之外
因為接下來的版本控制會以SVN為例，所以加入了SVN的版號%build.vcs.number%
Artifact Paths是最後產出檔案的路徑，先指向到Publish這個資料夾下面的zip檔
![](http://1.bp.blogspot.com/-0VQnfAkDWuM/UKJkDkGNBPI/AAAAAAAAAeE/Z_y0L8qvUb4/s1600/04.GeneralSetting.png)](http://1.bp.blogspot.com/-0VQnfAkDWuM/UKJkDkGNBPI/AAAAAAAAAeE/Z_y0L8qvUb4/s1600/04.GeneralSetting.png)</div>[
](http://3.bp.blogspot.com/-PJJeQCXAFHk/UKI-eIHs3DI/AAAAAAAAAZo/1JmD-gL3oSk/s1600/04.GeneralSetting.png)

## 第二步是設定一個版本控制來取得原始碼
![](http://4.bp.blogspot.com/-UkgcJOZkncQ/UKI-emmKCZI/AAAAAAAAAZw/dr9l8W2sPHQ/s1600/05.AddSVN.png)](http://4.bp.blogspot.com/-UkgcJOZkncQ/UKI-emmKCZI/AAAAAAAAAZw/dr9l8W2sPHQ/s1600/05.AddSVN.png)

## 下拉選單中有大部份Source Control的類型，這邊以SVN為例子
主要就是輸入路徑和帳號密碼就行了
![](http://1.bp.blogspot.com/-jJ6LldtRrGY/UKI-fGKSBpI/AAAAAAAAAZ4/O2YI_fnIPE4/s1600/06.ConfigSVN.png)](http://1.bp.blogspot.com/-jJ6LldtRrGY/UKI-fGKSBpI/AAAAAAAAAZ4/O2YI_fnIPE4/s1600/06.ConfigSVN.png)

## Labeling Rules這邊設定的是從trunk分支到tags的動作，等下還會有更詳細的設定
Test Connection可以測試一下是否可以連線，沒問題的話就按下Save按鈕
![](http://2.bp.blogspot.com/-6GoA44nrcIU/UKI-f91HcEI/AAAAAAAAAaA/spum8XecZxc/s1600/07.LabelingRule.png)](http://2.bp.blogspot.com/-6GoA44nrcIU/UKI-f91HcEI/AAAAAAAAAaA/spum8XecZxc/s1600/07.LabelingRule.png)

## 完成了一個VCS root的設定，順便編輯一下Checkout Rules
最簡單的用法就是每次只取出trunk的內容，並當成根目錄，就不會取出trunk和branches的資料了
![](http://3.bp.blogspot.com/-lhIOzEPYwGo/UKI-gphZzGI/AAAAAAAAAaI/cLETpRhADCE/s1600/08.AddCheckOutRule.png)](http://3.bp.blogspot.com/-lhIOzEPYwGo/UKI-gphZzGI/AAAAAAAAAaI/cLETpRhADCE/s1600/08.AddCheckOutRule.png)

## 接下來還有更詳細的設定
Clean all files before build是用來選擇是否在每次編譯之前都先清空svn的資料，重新下載
VCS Labeling mode是用來選擇，是否要在建置之後，來執行剛設定Labeling的動作
![](http://3.bp.blogspot.com/-QF04KvH5GD8/UKI-hhYbqxI/AAAAAAAAAaQ/QHHSjvDHF0U/s1600/09.AddCheckOutRuleOK.png)](http://3.bp.blogspot.com/-QF04KvH5GD8/UKI-hhYbqxI/AAAAAAAAAaQ/QHHSjvDHF0U/s1600/09.AddCheckOutRuleOK.png)

## Build Step是用來設定建置方式，這邊選擇用方案檔的方式來建置專案
因為用到了Package這個target來封裝專案，所以需要選擇專案檔而不是方案檔
希望建置後封裝的檔案可以產出在前面設定Artifact Paths的路徑中，所以額外設了一個參數 
如果一開始選擇用MSBuild來建置的話，參數的設定會更靈活
![](http://4.bp.blogspot.com/-HrWNHxrJr4k/UKJkQJN45nI/AAAAAAAAAeM/HBtGCa28xhs/s1600/10.SlnSetting.png)](http://4.bp.blogspot.com/-HrWNHxrJr4k/UKJkQJN45nI/AAAAAAAAAeM/HBtGCa28xhs/s1600/10.SlnSetting.png)
[](http://2.bp.blogspot.com/-T4I3Y-bAw6o/UKI-iAekUsI/AAAAAAAAAaY/j7XY3DU-VXY/s1600/10.SlnSetting.png)

## 到這裡已經設定好專案了，如果日後需要修改設定，可以直接按右邊的某一個步驟來調整
先按一下右上角的Run來跑跑看目前的設定正不正確，再按一下Build Configuration Home來看結果
![](http://1.bp.blogspot.com/-qC2tZAjzWIk/UKI-i2KJkpI/AAAAAAAAAag/kuJ0MGuRkK4/s1600/11.ConfigOK.png)](http://1.bp.blogspot.com/-qC2tZAjzWIk/UKI-i2KJkpI/AAAAAAAAAag/kuJ0MGuRkK4/s1600/11.ConfigOK.png)

## 可以看到這個專案的編譯記錄，目前編譯的版本，和SVN的送交記錄等等訊息
![](http://4.bp.blogspot.com/-32zzSpUlyws/UKJkcEg2LQI/AAAAAAAAAeU/W2FsTKGR3bQ/s1600/12.Run.png)](http://4.bp.blogspot.com/-32zzSpUlyws/UKJkcEg2LQI/AAAAAAAAAeU/W2FsTKGR3bQ/s1600/12.Run.png)
[](http://3.bp.blogspot.com/-_p1GLwTwRzs/UKI-jesn_OI/AAAAAAAAAao/fB02SYvs0Fc/s1600/12.Run.png)

## 編譯成功，也正確產出檔案的話，在Artifacts會有檔案下載的連結
![](http://3.bp.blogspot.com/-pFj39zNIxV0/UKJkgEv6tRI/AAAAAAAAAec/Z_VC5mEObtQ/s1600/13.Artifacts.png)](http://3.bp.blogspot.com/-pFj39zNIxV0/UKJkgEv6tRI/AAAAAAAAAec/Z_VC5mEObtQ/s1600/13.Artifacts.png)
[](http://2.bp.blogspot.com/-ph312JtgFQI/UKI-kIk4NGI/AAAAAAAAAaw/IK1FxVZAqWU/s1600/13.Artifacts.png)

## 參考資料
* [Continuous Integration &amp; Build Server – TeamCity (二) 設定專案](http://www.dotblogs.com.tw/kirkchen/archive/2010/08/10/17115.aspx)
* [Continuous builds with TeamCity ](http://www.troyhunt.com/2010/11/you-deploying-it-wrong-teamcity_25.html)