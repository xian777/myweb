---
title: 'Redis C# Client - StackExchange.Redis'
tags:
  - Redis
date: 2015-01-20 10:36:00
---

先透過NuGet安裝StackExchange.Redis這個套件
如果需要簽署的元件，可以安裝StackExchange.Redis.StrongName這個套件
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-5e3umPXt3g0/VL2_bYzn_sI/AAAAAAAACIo/y5oTaiwue3Q/s1600/01.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)](http://2.bp.blogspot.com/-5e3umPXt3g0/VL2_bYzn_sI/AAAAAAAACIo/y5oTaiwue3Q/s1600/01.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)</div>

透過ConnectionMultiplexer這個類別來產生連線，並重覆使用
再透過GetDatabase來取得要IDatabase介面，就可以存取Redis了
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using System;
    using StackExchange.Redis;

    class Program
    {
        static void Main(string[] args)
        {
            ConnectionMultiplexer conn = ConnectionMultiplexer.Connect("127.0.0.1:6379");
            IDatabase cache = conn.GetDatabase();
            cache.StringSet("key1", "value1");
            string data = cache.StringGet("key1");
            Console.WriteLine(data);
        }
    }
}
</pre></div>

參考資料

[StackExchange.Redis官網](https://github.com/StackExchange/StackExchange.Redis)