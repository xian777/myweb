---
title: certbot
date: 2018-09-14 14:25:42
tags:
---

# 申請wildcard憑證
透過docker執行以下指令
-d 指定網域
-m 指定申請人email
-v 把/etc/letsencrypt的資料對應到本機硬碟

```shell
docker run -it --rm -v /d/certs:/etc/letsencrypt certbot/certbot \
    certonly --manual \
    --preferred-challenges dns \
    --server https://acme-v02.api.letsencrypt.org/directory \
    -d *.developer.idv.tw \
    -m xian@developer.idv.tw
```
# 同意申請
![同意申請](01.png)

# 是否接受郵件通知
![是否接受郵件通知](02.png)

# 是否登錄申請IP
![是否登錄申請IP](03.png)

# 設定網域TXT
![設定網域TXT](04.png)

# 確認網域TXT已生效
![確認網域TXT已生效](05.png)

# 完成憑證申請
![完成憑證申請](06.png)

# 憑證位置
在archive資料夾下面
![憑證位置](07.png)

# 轉換憑證格式
打開[SSL Convert](https://www.sslshopper.com/ssl-converter.html)
選擇cert1.pem和privkey1.pem和chain1.pem
![轉成pfx格式](08.png)