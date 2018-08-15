---
title: Redis StoredSet
tags:
  - Redis
date: 2015-01-21 16:08:00
---

<table border="1" cellpadding="3" cellspacing="1"><tbody><tr><td>指令</td><td>說明</td></tr><tr><td>ZADD</td><td>將一個或多個元素加入有序集合</td></tr><tr><td>ZCARD</td><td>取得有序集合中的元素個數</td></tr><tr><td>ZCOUNT</td><td>取得有序集合中，score值在min到max的元素個數</td></tr><tr><td>ZINCRBY</td><td>設定有序集合中的成員score遞增值</td></tr><tr><td>ZRANGE</td><td>取得有序集合中指定位置範圍的元素</td></tr><tr><td>ZRANGEBYSCORE</td><td>取得有序集合中指定score範圍的元素</td></tr><tr><td>ZRANK</td><td>取得有序集合中元素從大到小的排列順序</td></tr><tr><td>ZREM</td><td>移除有序集合中一個或多個元素</td></tr><tr><td>ZREMRANGEBYRANK</td><td>移除有序集合中指定排名範圍的元素</td></tr><tr><td>ZREMRANGEBYSCORE</td><td>移除有序集合中指定score範圍的元素</td></tr><tr><td>ZREVRANGE</td><td>取得有序集合中指定位置範圍的元素
元素以遞減方式排列</td></tr><tr><td>ZREVRANGEBYSCORE</td><td>取得有序集合中指定score範圍的元素
元素以遞減方式排列</td></tr><tr><td>ZREVRANK</td><td>取得有序集合中元素從小到大的排列順序</td></tr><tr><td>ZSCORE</td><td>取得有序集點中元素的score值</td></tr><tr><td>ZUNIONSTORE</td><td>合併一個或多個有序集合的聯集
並把合併後的資料存成另一個有序集合</td></tr><tr><td>ZINTERSTORE</td><td>合併一個或多個有序集合的交集
並把合併後的資料存成另一個有序集合</td></tr><tr><td>ZSCAN</td><td>搜尋有序集合元素</td></tr><tr><td>ZRANGEBYLEX</td><td>取得有序集合中指定位置範圍的元素
當元素有相同的score時，用成員的字典順序排列</td></tr><tr><td>ZLEXCOUNT</td><td>取得有序集合中指定位置範圍的元素數量
當元素有相同的score時，用成員的字典順序排列</td></tr><tr><td>ZREMRANGEBYLEX</td><td>移除有序集合中指定排名範圍的元素
當元素有相同的score時，用成員的字典順序排列</td></tr></tbody></table>