---
title: TeamCity 發行 Octopus 部署套件
tags:
  - Octopus
  - TeamCity
date: 2014-09-29 17:37:00
---

先到Octopus建立一個專案
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-FDLLsc4giU4/VCkiHt_yQyI/AAAAAAAABrU/gvNiJ8w3SsI/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://4.bp.blogspot.com/-FDLLsc4giU4/VCkiHt_yQyI/AAAAAAAABrU/gvNiJ8w3SsI/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>
選擇發行套件
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Z8lhnIjJIxE/VCkiHiZxCGI/AAAAAAAABrc/XF7oPi2g3Mk/s1600/02.%E6%96%B0%E5%A2%9E%E6%AD%A5%E7%BD%B2Step.png)](http://2.bp.blogspot.com/-Z8lhnIjJIxE/VCkiHiZxCGI/AAAAAAAABrc/XF7oPi2g3Mk/s1600/02.%E6%96%B0%E5%A2%9E%E6%AD%A5%E7%BD%B2Step.png)</div>
就可以找到剛建置出來的套件
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Cwnpf4xmYks/VCkiHjpMRdI/AAAAAAAABrY/IL4ip64ddY8/s1600/03.%E9%81%B8%E6%93%87%E5%A5%97%E4%BB%B6.png)](http://4.bp.blogspot.com/-Cwnpf4xmYks/VCkiHjpMRdI/AAAAAAAABrY/IL4ip64ddY8/s1600/03.%E9%81%B8%E6%93%87%E5%A5%97%E4%BB%B6.png)</div>
回到TeamCity新增一個部署設定
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-2hVQBVI5FGg/VCkiIYd3vPI/AAAAAAAABrg/30Q4soZJvkU/s1600/04.%E6%96%B0%E5%A2%9E%E9%83%A8%E7%BD%B2%E5%B0%88%E6%A1%88.png)](http://1.bp.blogspot.com/-2hVQBVI5FGg/VCkiIYd3vPI/AAAAAAAABrg/30Q4soZJvkU/s1600/04.%E6%96%B0%E5%A2%9E%E9%83%A8%E7%BD%B2%E5%B0%88%E6%A1%88.png)</div>
在Trigger中新增一個建置完成觸發事件，指定到對應的專案
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-ROmAs_Tl5qY/VCkiIi3CO_I/AAAAAAAABrk/iNQEOH-dwKY/s1600/05.%E5%BB%BA%E7%BD%AETrigger%E6%96%B0%E5%A2%9E.png)](http://4.bp.blogspot.com/-ROmAs_Tl5qY/VCkiIi3CO_I/AAAAAAAABrk/iNQEOH-dwKY/s1600/05.%E5%BB%BA%E7%BD%AETrigger%E6%96%B0%E5%A2%9E.png)</div>
在關聯性設定中，也把這個專案指定進來
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-IaQZvFCbfA4/VCkiItMFcII/AAAAAAAABro/ppW2dwwNADI/s1600/06.%E6%96%B0%E5%A2%9E%E9%97%9C%E8%81%AF.png)](http://4.bp.blogspot.com/-IaQZvFCbfA4/VCkiItMFcII/AAAAAAAABro/ppW2dwwNADI/s1600/06.%E6%96%B0%E5%A2%9E%E9%97%9C%E8%81%AF.png)</div>
在版號的地方才能用%dep開頭的設定，取得這個專案目前的版號
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-mJjKvkDGHnE/VCkiI-EY_EI/AAAAAAAABrs/EL5AkEmhWyg/s1600/07.%E8%A8%AD%E5%AE%9A%E7%89%88%E8%99%9F.png)](http://3.bp.blogspot.com/-mJjKvkDGHnE/VCkiI-EY_EI/AAAAAAAABrs/EL5AkEmhWyg/s1600/07.%E8%A8%AD%E5%AE%9A%E7%89%88%E8%99%9F.png)</div>
建置步驟選擇OctopusDeploy: Create release
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-N3IP4kF2I58/VCkiJNkJraI/AAAAAAAABrw/57LbhpwOkfs/s1600/08.%E9%81%B8%E6%93%87%E5%BB%BA%E7%BD%AE%E9%83%A8%E7%BD%B2.png)](http://1.bp.blogspot.com/-N3IP4kF2I58/VCkiJNkJraI/AAAAAAAABrw/57LbhpwOkfs/s1600/08.%E9%81%B8%E6%93%87%E5%BB%BA%E7%BD%AE%E9%83%A8%E7%BD%B2.png)</div>
輸入Octopus URL和API Key
再輸入專案名稱和要連立版本的版號
如果要順便部署環境的話，就在Deploy To中輸入環境名稱
再把Wait for deployment to complete勾起來就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-O_2Habk45Yo/VCkiJQdQ-EI/AAAAAAAABr0/11DQQ0IDrPQ/s1600/09.%E8%A8%AD%E5%AE%9A%E5%BB%BA%E7%BD%AE.png)](http://1.bp.blogspot.com/-O_2Habk45Yo/VCkiJQdQ-EI/AAAAAAAABr0/11DQQ0IDrPQ/s1600/09.%E8%A8%AD%E5%AE%9A%E5%BB%BA%E7%BD%AE.png)</div>
建置成功
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-l4WiqDvB-9M/VCkiJqUgMiI/AAAAAAAABr4/tR0CZlH9JCA/s1600/10.%E5%BB%BA%E7%BD%AE%E6%88%90%E5%8A%9F.png)](http://1.bp.blogspot.com/-l4WiqDvB-9M/VCkiJqUgMiI/AAAAAAAABr4/tR0CZlH9JCA/s1600/10.%E5%BB%BA%E7%BD%AE%E6%88%90%E5%8A%9F.png)</div>
自動新增一個部署版本了
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-EyAfvTISWyA/VCkiJ--PefI/AAAAAAAABr8/DDiX9HZ9I-4/s1600/11.%E7%99%BC%E8%A1%8C%E6%88%90%E5%8A%9F.png)](http://1.bp.blogspot.com/-EyAfvTISWyA/VCkiJ--PefI/AAAAAAAABr8/DDiX9HZ9I-4/s1600/11.%E7%99%BC%E8%A1%8C%E6%88%90%E5%8A%9F.png)</div>