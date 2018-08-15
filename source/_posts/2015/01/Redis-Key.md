---
title: Redis Key
tags:
  - Redis
date: 2015-01-20 11:05:00
---

<table border="1" cellpadding="3" cellspacing="1"><tbody><tr><td>指令</td><td>說明</td></tr><tr><td>DEL</td><td>刪除指定的Key</td></tr><tr><td>DUMP</td><td>將指定key的內容匯出二進位內容
配合RESTORE指令可以把資料還原</td></tr><tr><td>EXISTS</td><td>判斷指定的Key是否存在</td></tr><tr><td>EXPIRE</td><td>用來設定Key的過期時間，單位是秒</td></tr><tr><td>EXPIREAT</td><td>用來設定Key的過期時間，單位是秒，UNIX時間戳記</td></tr><tr><td>KEYS</td><td>用來查詢目前Redis實體上的Key
可配合pattern查詢</td></tr><tr><td>MIGRATE</td><td>搬移資料到不同的Redis執行個體</td></tr><tr><td>MOVE</td><td>將指定的Key值搬到同一個Redis執行個體的不同資料庫</td></tr><tr><td>OBJECT</td><td>用來顯示該Key值的特性
OBJECT REFCOUNT &lt;key&gt; 取得該key的異動次數
OBJECT ENCODING &lt;key&gt; 取得該key的編碼
OBJECT IDLETIME &lt;key&gt; 取得該key未被存取的秒數</td></tr><tr><td>PERSIST</td><td>取消KEY上面的過期時間</td></tr><tr><td>PEXPIRE</td><td>用來設定Key的過期時間，單位是毫秒</td></tr><tr><td>PEXPIREAT</td><td>用來設定Key的過期時間，單位是毫秒，UNIX時間戳記</td></tr><tr><td>PTTL</td><td>取得Key到期的剩餘時間，單位是毫秒</td></tr><tr><td>RANDOMKEY</td><td>隨機取得一個Key</td></tr><tr><td>RENAME</td><td>更名Key的名稱，如果新名稱已存在會覆蓋</td></tr><tr><td>RENAMENX</td><td>當key的新名稱不存在時，才更名Key的名稱</td></tr><tr><td>RESTORE</td><td>配合DUMP指令匯出的二進位內容
用來把資料還原</td></tr><tr><td>SORT</td><td>排序指定key的內容
配合limit可限制筆數

</td></tr><tr><td>TTL</td><td>取得Key到期的剩餘時間，單位是秒</td></tr><tr><td>TYPE</td><td>取得指定Key的內容的資料型態</td></tr><tr><td>SCAN</td><td>搜尋Key，可配合pattern
返回結果是一個迭代的指標</td></tr></tbody></table>