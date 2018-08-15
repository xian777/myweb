---
title: Octopus部署專案
tags:
  - Octopus
date: 2012-11-05 21:36:00
---

## 首先設定一下NuGet套件的來源，在設定中選擇NuGet，再點擊Add NuGet feed
![](http://2.bp.blogspot.com/-eB-5_jr8Tco/UJe-gvfxniI/AAAAAAAAARs/Uf5vQaP2B9k/s1600/01.AddNuGetFeed.png)](http://2.bp.blogspot.com/-eB-5_jr8Tco/UJe-gvfxniI/AAAAAAAAARs/Uf5vQaP2B9k/s1600/01.AddNuGetFeed.png)

## 輸入名稱和NuGet Server所在位置，如有需要授權就再輸入帳密，然後按下新增
![](http://3.bp.blogspot.com/-p-KdXHP_KvA/UJe-hAxku4I/AAAAAAAAAR0/_NYIRdWHbks/s1600/02.SaveNuGetFeed.png)](http://3.bp.blogspot.com/-p-KdXHP_KvA/UJe-hAxku4I/AAAAAAAAAR0/_NYIRdWHbks/s1600/02.SaveNuGetFeed.png)

## 接下來先建立專案群組
![](http://2.bp.blogspot.com/-_xbwdU3aDvA/UJe-hmD6DmI/AAAAAAAAAR8/E_rbSdD6ous/s1600/03.ProjGroup.png)](http://2.bp.blogspot.com/-_xbwdU3aDvA/UJe-hmD6DmI/AAAAAAAAAR8/E_rbSdD6ous/s1600/03.ProjGroup.png)

## 再來選擇建立專案
![](http://2.bp.blogspot.com/-4gsASjDPLTU/UJe-iecxQoI/AAAAAAAAASE/qEAzaQGrxGg/s1600/04.CreateProj.png)](http://2.bp.blogspot.com/-4gsASjDPLTU/UJe-iecxQoI/AAAAAAAAASE/qEAzaQGrxGg/s1600/04.CreateProj.png)

## 輸入專案資訊
![](http://4.bp.blogspot.com/-ZAwObqAo_KM/UJe-ivPrxWI/AAAAAAAAASM/OtkrLc6EIzc/s1600/05.AddProj.png)](http://4.bp.blogspot.com/-ZAwObqAo_KM/UJe-ivPrxWI/AAAAAAAAASM/OtkrLc6EIzc/s1600/05.AddProj.png)

## 新增完成，點擊專案名稱來設定部署
![](http://3.bp.blogspot.com/-OUKY0O9Ysoo/UJe-jGQvxYI/AAAAAAAAASU/RGDhTl0smos/s1600/06.AddProjSuccess.png)](http://3.bp.blogspot.com/-OUKY0O9Ysoo/UJe-jGQvxYI/AAAAAAAAASU/RGDhTl0smos/s1600/06.AddProjSuccess.png)

## 選擇Steps，再點擊Add package step
![](http://2.bp.blogspot.com/-gRHt3_sxa-0/UJe-j1SAj4I/AAAAAAAAASc/pjn3CciupCU/s1600/07.Steps.png)](http://2.bp.blogspot.com/-gRHt3_sxa-0/UJe-j1SAj4I/AAAAAAAAASc/pjn3CciupCU/s1600/07.Steps.png)

## 輸入套件資料，如果專案有多個套件，可重覆此步驟
![](http://4.bp.blogspot.com/-aau7ZAIqhzo/UJe-kJ3IBsI/AAAAAAAAASk/RJ22IWIbMug/s1600/08.AddStep.png)](http://4.bp.blogspot.com/-aau7ZAIqhzo/UJe-kJ3IBsI/AAAAAAAAASk/RJ22IWIbMug/s1600/08.AddStep.png)

## 接下來建立發佈版本
![](http://1.bp.blogspot.com/-Q3sIi82aRWg/UJe-k7H2nEI/AAAAAAAAASs/FB5PLU39KK4/s1600/09.CreateRelease.png)](http://1.bp.blogspot.com/-Q3sIi82aRWg/UJe-k7H2nEI/AAAAAAAAASs/FB5PLU39KK4/s1600/09.CreateRelease.png)

## 輸入版本資訊
![](http://4.bp.blogspot.com/-7hmX0qXpuP8/UJe-lqezpeI/AAAAAAAAAS0/s1zlTX_NIps/s1600/10.AddPack.png)](http://4.bp.blogspot.com/-7hmX0qXpuP8/UJe-lqezpeI/AAAAAAAAAS0/s1zlTX_NIps/s1600/10.AddPack.png)

## 發佈版本資訊
![](http://3.bp.blogspot.com/-7NdYKSQqG9s/UJe-mEzRh5I/AAAAAAAAAS8/_7dyWOdaW9Q/s1600/11.Deploy.png)](http://3.bp.blogspot.com/-7NdYKSQqG9s/UJe-mEzRh5I/AAAAAAAAAS8/_7dyWOdaW9Q/s1600/11.Deploy.png)

## 執行發佈版本
![](http://2.bp.blogspot.com/-TAKCxk9v-tA/UJe-m1BFQCI/AAAAAAAAATE/3RJ0pHpepHQ/s1600/12.DeployPackage.png)](http://2.bp.blogspot.com/-TAKCxk9v-tA/UJe-m1BFQCI/AAAAAAAAATE/3RJ0pHpepHQ/s1600/12.DeployPackage.png)

## 發佈成功
![](http://1.bp.blogspot.com/-TDX71V5yrrY/UJe-nIkvpYI/AAAAAAAAATM/du0maFJdsSs/s1600/13.DeploySuccess.png)](http://1.bp.blogspot.com/-TDX71V5yrrY/UJe-nIkvpYI/AAAAAAAAATM/du0maFJdsSs/s1600/13.DeploySuccess.png)