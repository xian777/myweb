---
title: 安裝Octopus Tentacle
tags:
  - Octopus
date: 2012-11-05 20:13:00
---

## 首先到官網下載Tentacle安裝程式
![](http://2.bp.blogspot.com/-23up0pJpYA8/UJeslHAt-1I/AAAAAAAAAPk/rNtz5vZ9vI8/s1600/00.Files.png)](http://2.bp.blogspot.com/-23up0pJpYA8/UJeslHAt-1I/AAAAAAAAAPk/rNtz5vZ9vI8/s1600/00.Files.png)

## 一直按下一步就可以完成安裝了
![](http://4.bp.blogspot.com/-iLmkFkUJ7Ss/UJesluMrZmI/AAAAAAAAAPs/XQ__Y070zrw/s1600/01.Install.png)](http://4.bp.blogspot.com/-iLmkFkUJ7Ss/UJesluMrZmI/AAAAAAAAAPs/XQ__Y070zrw/s1600/01.Install.png)

## 接下來進入設定畫面，這裡的信任key要從剛安裝的網站上取得
![](http://2.bp.blogspot.com/-2Zn6TeCZlSU/UJesmFKNP1I/AAAAAAAAAP0/YgSc8eNFe5o/s1600/02.Client.png)](http://2.bp.blogspot.com/-2Zn6TeCZlSU/UJesmFKNP1I/AAAAAAAAAP0/YgSc8eNFe5o/s1600/02.Client.png)

## 先建一個環境出來
![](http://3.bp.blogspot.com/-Jye8t4XHAPk/UJesm4wStcI/AAAAAAAAAP8/QCS7jTpZP34/s1600/03.EnvirAdd.png)](http://3.bp.blogspot.com/-Jye8t4XHAPk/UJesm4wStcI/AAAAAAAAAP8/QCS7jTpZP34/s1600/03.EnvirAdd.png)

## 再建一個機器，把Tentacle的Key打上去</div>Thumbprint就是要打到Tentacle去的Key
## Roles輸入機器的用途，這邊以WebServer為例
![](http://1.bp.blogspot.com/-qErkwlnaUtg/UJesncGhhuI/AAAAAAAAAQE/fCZqO4Ua6u0/s1600/04.AddMachine.png)](http://1.bp.blogspot.com/-qErkwlnaUtg/UJesncGhhuI/AAAAAAAAAQE/fCZqO4Ua6u0/s1600/04.AddMachine.png)

## 再回到Tentacle的設定畫面，這邊是部署過來的資料要存放的地方
![](http://4.bp.blogspot.com/-pKa_a3Nn6qI/UJesn-5iwxI/AAAAAAAAAQM/mn_Bo-idNpI/s1600/05.ClientLocation.png)](http://4.bp.blogspot.com/-pKa_a3Nn6qI/UJesn-5iwxI/AAAAAAAAAQM/mn_Bo-idNpI/s1600/05.ClientLocation.png)

## Tentacle的Service，按下Install就行了
![](http://3.bp.blogspot.com/-P1ConmMDXMo/UJesoVX8gVI/AAAAAAAAAQU/eHXVH7AnDxI/s1600/06.ClientService.png)](http://3.bp.blogspot.com/-P1ConmMDXMo/UJesoVX8gVI/AAAAAAAAAQU/eHXVH7AnDxI/s1600/06.ClientService.png)

## 回到網站，按一下Check health，順利的話就會看到剛設定的Machine可以使用了
![](http://1.bp.blogspot.com/-yM3_QMYevIA/UJespGj3ikI/AAAAAAAAAQc/tckJLMtWuJg/s1600/07.OK.png)](http://1.bp.blogspot.com/-yM3_QMYevIA/UJespGj3ikI/AAAAAAAAAQc/tckJLMtWuJg/s1600/07.OK.png)