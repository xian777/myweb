---
title: 透過Application Request Route來做SSL offloading
tags: []
date: 2016-05-08 12:23:00
---

# Application Request Route
越來越多站台要開始使用SSL了, 記錄一下使用Application Request Route來做SSL offloading的用法

## 首先透過Web Platform Installer來安裝ARR
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-ElT4qkQUCMg/Vy6-1AwXW9I/AAAAAAAADwo/F5deoTLNuUYZCXB6Wa9fWioG_MkC_12nQCLcB/s1600/01.png)](https://1.bp.blogspot.com/-ElT4qkQUCMg/Vy6-1AwXW9I/AAAAAAAADwo/F5deoTLNuUYZCXB6Wa9fWioG_MkC_12nQCLcB/s1600/01.png)</div>

## 搜尋Application Request Routing, 找到後點安裝就行了
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-PqGjDtVXRKE/Vy6-1HeRtPI/AAAAAAAADws/8USKKPPzNtszIbaUSy_KROwdUHAo6C1LACLcB/s1600/02.png)](https://2.bp.blogspot.com/-PqGjDtVXRKE/Vy6-1HeRtPI/AAAAAAAADws/8USKKPPzNtszIbaUSy_KROwdUHAo6C1LACLcB/s1600/02.png)</div>

## 重新打開IIS會看到新增了Server Farms和ARR和URL Rewrite這幾個功能
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-SAnm-5fysLo/Vy6-09HaEuI/AAAAAAAADwk/UdlVYz0Cm3Yz9x0uXyEcxvxeV9mQS_WAwCLcB/s1600/03.png)](https://3.bp.blogspot.com/-SAnm-5fysLo/Vy6-09HaEuI/AAAAAAAADwk/UdlVYz0Cm3Yz9x0uXyEcxvxeV9mQS_WAwCLcB/s1600/03.png)</div>

## 先建立一個預設的站台來繫結https通訊協定
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-wOACJ9Oz_Dk/Vy6-1ZMCEnI/AAAAAAAADww/HrE4keo33UkK3nuuMhXIFyQrWz18IELSgCLcB/s1600/04.png)](https://4.bp.blogspot.com/-wOACJ9Oz_Dk/Vy6-1ZMCEnI/AAAAAAAADww/HrE4keo33UkK3nuuMhXIFyQrWz18IELSgCLcB/s1600/04.png)</div>

## 只有預設站台是HTTPS, 其他站台都是HTTP
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-JApbMNiN87M/Vy6-1iZNSmI/AAAAAAAADw4/wr7iijiMFoAZzzJFxZ5LLncz7yWhoEJ7ACLcB/s1600/05.png)](https://2.bp.blogspot.com/-JApbMNiN87M/Vy6-1iZNSmI/AAAAAAAADw4/wr7iijiMFoAZzzJFxZ5LLncz7yWhoEJ7ACLcB/s1600/05.png)</div>

## 建立一組Server Farms
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-W1G06hP7xQc/Vy6-1ekSG8I/AAAAAAAADw0/brdiY-EUg4I5eOFOqdL0FnY90qX3UuvJwCLcB/s1600/06.png)](https://1.bp.blogspot.com/-W1G06hP7xQc/Vy6-1ekSG8I/AAAAAAAADw0/brdiY-EUg4I5eOFOqdL0FnY90qX3UuvJwCLcB/s1600/06.png)</div>

## 建立一條路由規則來強制站台只能使用https通訊協定
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-TzVI_c6eXAE/Vy6-1pAPevI/AAAAAAAADw8/-1-hgZkbNIY8HC0WhcKZevo6giJ6hF--QCLcB/s1600/07.png)](https://3.bp.blogspot.com/-TzVI_c6eXAE/Vy6-1pAPevI/AAAAAAAADw8/-1-hgZkbNIY8HC0WhcKZevo6giJ6hF--QCLcB/s1600/07.png)</div>

## 建立第二條路由規則來處理SSL offloading路由到原來只繫結http的站台
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-f_vIIp3UtEY/Vy6-1z0koVI/AAAAAAAADxA/AuXVhz2ecYwiHH8q-z97tLFavcCzRRPLwCLcB/s1600/08.png)](https://2.bp.blogspot.com/-f_vIIp3UtEY/Vy6-1z0koVI/AAAAAAAADxA/AuXVhz2ecYwiHH8q-z97tLFavcCzRRPLwCLcB/s1600/08.png)</div>

## http就會自動轉向https囉
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-1kiW1jBNV6Q/Vy6-12TzbqI/AAAAAAAADxE/GNepJK2W28o8JPGYSd3YIgk_BzylUCDvwCLcB/s1600/09.png)](https://2.bp.blogspot.com/-1kiW1jBNV6Q/Vy6-12TzbqI/AAAAAAAADxE/GNepJK2W28o8JPGYSd3YIgk_BzylUCDvwCLcB/s1600/09.png)</div>