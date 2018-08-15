---
title: 'C# HexString to ByteArray'
tags:
  - 'C#'
date: 2015-03-04 15:43:00
---

16進位的字串轉成ByteArray

<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using System;
    using System.Linq;

    class Program
    {
        static void Main(string[] args)
        {
            string hexstring = "0123456789abcdef";
            byte[] byteArray = Enumerable.Range(0, hexstring.Length)
                .Where(x =&gt; x % 2 == 0)
                .Select(x =&gt; Convert.ToByte(hexstring.Substring(x, 2), 16))
                .ToArray();
            Console.WriteLine(BitConverter.ToString(byteArray));
        }
    }
}
</pre></div>