---
title: Redis 設定檔
tags:
  - Redis
date: 2015-01-19 19:13:00
---

用來指派空間的單位簡寫，不區分大小寫
# 1k =&gt; 1000 bytes
# 1kb =&gt; 1024 bytes
# 1m =&gt; 1000000 bytes
# 1mb =&gt; 1024*1024 bytes
# 1g =&gt; 1000000000 bytes
# 1gb =&gt; 1024*1024*1024 bytes

伺服器埠號
port 6379

繫結位址，預設是本機全部
# bind 127.0.0.1

Client連線閒置多久要切斷連線，單位為秒，0是不限制時間
timeout 0

################################ 快照設定 &nbsp;#################################
第一個參數是秒數，第二個參數是異動次數
符合以下任一條件，就執行一次快照，產生dump.rdb

save 900 1
save 300 10
save 60 10000

產生快照檔時是否要壓縮檔案
rdbcompression yes

快照檔案的檔名
dbfilename dump.rdb

快照檔案的路徑
dir ./

################################# 覆寫 #################################

在slave的實體上，用來指定master的位址
# slaveof &lt;masterip&gt; &lt;masterport&gt;

如果master需要驗證密碼時設定
# masterauth &lt;master-password&gt;

當slave和master斷線，或是正在同步中，是否回應Client端要求
設定成no會回應一個SYNC with master in progress的錯誤
slave-serve-stale-data yes

設定slave是否唯讀
slave-read-only yes
<div>
</div>slave對master實體ping的時間間隔，單位是秒數
# repl-ping-slave-period 10

master傳輸或是ping回應的時間間隔，單位是秒數
# repl-timeout 60

slave和master同步後，是否要延遲同步，讓master合併小封包再一回氣同步到slave
效能較佳，但資料可能不同步
repl-disable-tcp-nodelay no

slave優先權，當master無法服務時，數字低的優先被提升為master
slave-priority 100

################################## 安全 ###################################

Client連線時是否需要密碼
# requirepass foobared

重寫命令，設定成空字串來禁用命令
# rename-command CONFIG ""

################################### 限制 ####################################

最大連線數
# maxclients 10000

最大記憶體
# maxmemory &lt;bytes&gt;

當記憶體達到上限，使用那一種刪除演算法
# volatile-lru：使用LRU演算法刪除帶有過期標記的key
# allkeys-lru：使用LRU演算法刪除任何Key
# volatile-random：隨機移除一個帶有過期標記的Key
# allkeys-random：隨機移除一個Key
# volatile-ttl：移除快要過期的Key
# noeviction：不移除Key，回應一個錯誤給Client端
預設為volatile-lru
# maxmemory-policy volatile-lru

LRU演算法的樣本範圍
# maxmemory-samples 3
<div>
############################## AOF模式 ##########################

是否啟用AOF持久化模式
appendonly no

AOF模式的檔案名稱
# appendfilename appendonly.aof

AOF模式的寫入時機
no：由作業系統決定，性能最好，可靠性最低
everysec：每秒執行一次寫入
always：每次都寫入硬碟，效能最差
# appendfsync always
appendfsync everysec
# appendfsync no

在阻塞命令時阻止faync在主程序中被呼叫
no-appendfsync-on-rewrite no

AOF自動重寫設定，把重覆的命令合併以減少檔案大小
auto-aof-rewrite-percentage 100
auto-aof-rewrite-min-size 64mb

################################ LUA 腳本 &nbsp;###############################
lua腳本的最大執行時間，單位是毫秒
lua-time-limit 5000

################################## SLOW LOG ###################################
用來記錄超出執行時間的命令，單位為微秒，10000等於1秒
slowlog-log-slower-than 10000

slowlog的長度，超過設定長度後，最舊的會被移除
slowlog-max-len 128

############################### 進階設定 ###############################
設定hash的資料超過多少數量時，切換使用的數據結構
hash-max-ziplist-entries 512
hash-max-ziplist-value 64

設定list的資料超過多少數量時，切換使用的數據結構
list-max-ziplist-entries 512
list-max-ziplist-value 64

設定set的資料超過多少數量時，切換使用的數據結構
set-max-intset-entries 512

設定stored set的資料超過多少數量時，切換使用的數據結構
zset-max-ziplist-entries 128
zset-max-ziplist-value 64

hash是否使用延遲刷新機制，越多操作，越多刷新
activerehashing yes

第一個參數是強制限制，第二個參數是軟性限制，和軟性時間
當客戶輸出緩存達到限制時，會強制斷開連線
client-output-buffer-limit normal 0 0 0
client-output-buffer-limit slave 256mb 64mb 60
client-output-buffer-limit pubsub 32mb 8mb 60

背景任務執行頻率，範圍為1到500，預設為10
設定越大，CPU消耗越大，延遲越小
hz 10

啟用子行程重寫AOF檔案
aof-rewrite-incremental-fsync yes

</div>