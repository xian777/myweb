---
title: Docker on linux
tags:
  - docker
date: 2016-10-05 08:56:00
---

# Docker on linux

# 前置條件
* kernal 3.8以上
* 64位元

# 安裝腳本

```
curl -fsSL https://get.docker.com/ | sh
```

# 安裝完成

* 如果不是用root執行docker的話，記得加入帳號執行docker的權限
```
sudo usermod -aG docker your-user
```

<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-ekabkWpPcWs/V_RShADmG0I/AAAAAAAAEKE/Xm5jigPW7lcVxm_7AhqYRm8IPE2vlPnDACLcB/s1600/linux.png)](https://3.bp.blogspot.com/-ekabkWpPcWs/V_RShADmG0I/AAAAAAAAEKE/Xm5jigPW7lcVxm_7AhqYRm8IPE2vlPnDACLcB/s1600/linux.png)</div>

# 移除安裝
```
sudo apt-get purge docker-engine
sudo apt-get autoremove --purge docker-engine
sudo apt-get autoclean
sudo rm -rf /var/lib/docker
```