---
title: Redis List
tags:
  - Redis
date: 2015-01-20 11:42:00
---

<table border="1" cellpadding="3" cellspacing="1"><tbody><tr><td>指令</td><td>說明</td></tr><tr><td>BLPOP</td><td>阻塞式指令，從開頭彈出內容</td></tr><tr><td>BRPOP</td><td>阻塞式指令，從尾端彈出內容</td></tr><tr><td>BRPOPLPUSH</td><td>阻塞式指令，從尾端彈出內容，並把彈出的內容加入一個List的頭部</td></tr><tr><td>LINDEX</td><td>取得List中指定位置的內容</td></tr><tr><td>LINSERT</td><td>配合AFTER和BEFORE來決定插入指定位置的前面或後面</td></tr><tr><td>LLEN</td><td>取得List的長度</td></tr><tr><td>LPOP</td><td>從開頭彈出資料</td></tr><tr><td>LPUSH</td><td>從開頭加入資料</td></tr><tr><td>LPUSHX</td><td>從開頭加入資料，只有當鍵值存在並且是一個List的時後才成功</td></tr><tr><td>LRANGE</td><td>取得指定範圍內的資料</td></tr><tr><td>LREM</td><td>移除和指定內容相同的元素和個數</td></tr><tr><td>LSET</td><td>設定指定的資料</td></tr><tr><td>LTRIM</td><td>只保留指定範圍內的資料，不在指定範圍的資料全部移除</td></tr><tr><td>RPOP</td><td>從尾部彈出資料</td></tr><tr><td>RPOPLPUSH</td><td>從尾部彈出資料，並把彈出的資料加入一個List的頭部</td></tr><tr><td>RPUSH</td><td>從尾部加入資料</td></tr><tr><td>RPUSHX</td><td>從尾部加入資料，只有當鍵值存在並且是一個List的時後才成功</td></tr></tbody></table>