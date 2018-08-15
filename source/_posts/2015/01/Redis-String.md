---
title: Redis String
tags:
  - Redis
date: 2015-01-20 11:23:00
---

<table border="1" cellpadding="3" cellspacing="1"><tbody><tr><td>指令</td><td>說明</td></tr><tr><td>APPEND</td><td>拼接字串</td></tr><tr><td>BITCOUNT</td><td>計算字串中的二進位值被設成1的個數</td></tr><tr><td>BITOP</td><td>字串中的二進位值的位元操作</td></tr><tr><td>DECR</td><td>遞減值一</td></tr><tr><td>DECRBY</td><td>遞減指定的值</td></tr><tr><td>GET</td><td>取得指定鍵值的內容</td></tr><tr><td>GETBIT</td><td>取得指定鍵值的二進位內容</td></tr><tr><td>GETRANGE</td><td>取得指定鍵值的資料特定位置的內容</td></tr><tr><td>GETSET</td><td>設定指定鍵值的內容，並返回舊值</td></tr><tr><td>INCR</td><td>遞增值一</td></tr><tr><td>INCRBY</td><td>遞增指定的值</td></tr><tr><td>INCRBYFLOAT</td><td>遞增指定的浮點數值</td></tr><tr><td>MGET</td><td>一次取回多組指定的key value</td></tr><tr><td>MSET</td><td>一次設定多組key value</td></tr><tr><td>MSETNX</td><td>一次設定多組key value，並且所有設定的key都不存在才成功</td></tr><tr><td>PSETEX</td><td>設定key value，並指定過期時間，單位是毫秒</td></tr><tr><td>SET</td><td>設定key value
配合ex參數設定過期時間，單位是秒
配合px參數設定過期時間，單位是毫秒
配合nx參數只有key不存在時才成功
配合xx參數只有key已存在時才成功</td></tr><tr><td>SETBIT</td><td>設定指定鍵值的二進位資料</td></tr><tr><td>SETEX</td><td>設定key value，並指定過期時間，單位是秒</td></tr><tr><td>SETNX</td><td>設定key value，並只有在key不存在時才成功</td></tr><tr><td>SETRANGE</td><td>更改特定位置的資料內容</td></tr><tr><td>STRLEN</td><td>取得指定鍵值的內容長度</td></tr></tbody></table>