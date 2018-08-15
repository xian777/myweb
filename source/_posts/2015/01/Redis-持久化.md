---
title: Redis 持久化
tags:
  - Redis
date: 2015-01-21 16:26:00
---

Redis有兩種持久化方式，一種是RDB，一種是Append，可同時使用
RDB是定時快照，觸發條件發生時，會把當時記憶體的資料存成檔案
所以一旦發生故障，損失的資料較多

啟用RDB持久化
# save 900 1
# save 300 10
# save 60 10000

關閉RDB持久化
# &nbsp; save ""

設定是否可以壓縮
rdbcompression yes

設定RDB的檔名
dbfilename dump.rdb

設定檔案的資料夾位置
dir ./

===============================================
AOF是把收到的指令，用純文字檔的方式附加到檔案中，資料持久化的效能較完整

啟用AOF持久化
# appendonly no

AOF檔案名稱
# appendfilename appendonly.aof

AOF檔案寫入的方式
# appendfsync always
appendfsync everysec
# appendfsync no

設定AOF檔案重整的時間
auto-aof-rewrite-percentage 100
auto-aof-rewrite-min-size 64mb