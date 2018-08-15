---
title: AutoMapper 4.2 API Update
tags:
  - AutoMapper
date: 2016-02-28 18:01:00
---

<div>AutoMapper 4.2版本之後，將Mapper靜態API類別標注為過時，改用MapperConfiguration來設定對應，記錄一下新的使用方式</div>
首先宣告一個MapperConfiguration物件，並且設定類別對應關系
<div>

    var config = new MapperConfiguration(cfg =&gt; cfg.CreateMap&lt;Order, OrderDto&gt;());`</pre></div><div>使用的時後，透過CreateMapper建立一個IMapper物件
    再透過IMapper物件來轉換類別</div><pre style="background-color: #f7f7f7; border-radius: 3px; box-sizing: border-box; color: #333333; font-family: Consolas, 'Liberation Mono', Menlo, Courier, monospace; font-size: 13.6px; font-stretch: normal; line-height: 1.45; margin-bottom: 16px; overflow: auto; padding: 16px; word-wrap: normal;">`var mapper = config.CreateMapper();
    OrderDto dto = mapper.Map&lt;OrderDto&gt;(order);