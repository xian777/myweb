---
title: docker images
date: 2018-06-10 15:25:16
tags:
---
# 查詢docker hub上的images
```
$sudo docker search redis
```

# 查詢目前電腦的images
```
$sudo docker images
```

# 拉取images
```
$sudo docker pull redis:3.2.10
```

# 更名images
```
$sudo docker tag redis:3.2.10 myredis:1.2.3
```

# 在本機commit新版本
```
$sudo docker commit -m "commit my redis"
```

# 查詢commit記錄
```
$sudo docker history redis:3.2.10
```

# images存成檔案
```
$sudo docker save redis:3.2.10 -o redis.tar
```

# 檔案匯入images
```
$sudo docker load -i redis.tar
```

# 刪除images
```
$sudo docker rmi redis:3.2.10
```

# 登入Registry
```
$sudo docker login
```

# 登出Registry
```
$sudo docker logout
```

# 從Dockerfile編譯images
```
$sudo docker build -t ImageName:tag .
```