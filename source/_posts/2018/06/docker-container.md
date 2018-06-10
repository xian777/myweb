---
title: docker container
date: 2018-06-10 15:27:41
tags:
---

# 建立一個新容器
```
$sudo docker create redis:3.2.10
```

# 啟動容器
```
$sudo docker start <guid>
```

# 建立並啟動容器
```
$sudo docker run redis:3.2.10
```

# 查詢本機容器
```
$sudo docker ps -a
```

# 對應本機port
```
$sudo docker run -p 6379:6379 redis:3.2.10
```

# 對應本機硬碟
```
$sudo docker run -v /d/redis:/data redis:3.2.10
```

# 附加容器執行緒
```
$sudo docker attach <guid>
```

# 執行容器命令
```
$sudo docker exec -it <guid> bash
```

# 查詢容器資訊
```
$sudo docker inspect <guid>
```

# 暫停容器
```
$sudo docker pause <guid>
```

# 停止容器
```
$sudo docker stop <guid>
```

# 強制關閉容器
```
$sudo docker kill <guid>
```
# 刪除容器
```
$sudo rm <guid>
```