---
title: TopShelf
tags:
  - NuGet套件
  - windows service
date: 2016-01-27 11:50:00
---

開發Windows Service的時後，為了開發方便，之前都用一些小技巧切換在本機的Console模式和伺服器的Service模式，但在日後維護的時後或是偵錯的時後，總是不太方便，最近用了一個好用的套件叫TopShelf，是一個用來開發Windows Service的框架，實在太好用了，所以記錄一下筆記

首先新增一個Console專案
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-b-j_Dv8q9Y0/Vqg97bx32-I/AAAAAAAADkE/QVrxbWArdXg/s1600/01.%25E6%2596%25B0%25E5%25A2%259E%25E5%25B0%2588%25E6%25A1%2588.png)](http://2.bp.blogspot.com/-b-j_Dv8q9Y0/Vqg97bx32-I/AAAAAAAADkE/QVrxbWArdXg/s1600/01.%25E6%2596%25B0%25E5%25A2%259E%25E5%25B0%2588%25E6%25A1%2588.png)</div>
透過NuGet安裝TopShelf套件
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-0rrhnPEnOBU/Vqg97v3I74I/AAAAAAAADkQ/3I4zfXvgEYg/s1600/02.%25E5%25AE%2589%25E8%25A3%259D%25E5%25A5%2597%25E4%25BB%25B6.png)](http://4.bp.blogspot.com/-0rrhnPEnOBU/Vqg97v3I74I/AAAAAAAADkQ/3I4zfXvgEYg/s1600/02.%25E5%25AE%2589%25E8%25A3%259D%25E5%25A5%2597%25E4%25BB%25B6.png)</div>
簡單地寫一個類別，包含Start和Stop兩個函式
<div><pre class="brush:csharp">using System;

namespace ConsoleApplication1
{
    class MyService
    {
        public void Start()
        {
            Console.WriteLine("MyService Start");
        }

        public void Stop()
        {
            Console.WriteLine("My Service Stop");
        }
    }
}

</pre></div>
回到應用程式進入點開始配置服務
<div><pre class="brush:csharp">using Topshelf;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Topshelf.HostFactory.Run(x=&gt;
            {
                x.Service&lt;MyService&gt;(s =&gt;
                {
                    s.ConstructUsing(() =&gt; new MyService());
                    s.WhenStarted(svc =&gt; svc.Start());
                    s.WhenStopped(svc =&gt; svc.Stop());
                });

                x.RunAsLocalSystem();
                x.StartAutomatically();
                x.SetServiceName("MyService");
                x.SetDisplayName("MyService Display Name");
                x.SetDescription("MyService Description");
            });
        }
    }
}

</pre></div>
本機執行的結果
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-GkrSRu9YLU4/Vqg_kHL4ehI/AAAAAAAADkg/LahcDKUIdWU/s1600/05.%25E6%259C%25AC%25E6%25A9%259F%25E5%259F%25B7%25E8%25A1%258C.png)](http://1.bp.blogspot.com/-GkrSRu9YLU4/Vqg_kHL4ehI/AAAAAAAADkg/LahcDKUIdWU/s1600/05.%25E6%259C%25AC%25E6%25A9%259F%25E5%259F%25B7%25E8%25A1%258C.png)</div>
安裝服務只要在執行檔後面加上install參數就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-6rLO7_yoe6w/Vqg971lJ8GI/AAAAAAAADkM/uGAQ8bsxYb8/s1600/06.%25E5%25AE%2589%25E8%25A3%259D%25E6%259C%258D%25E5%258B%2599.png)](http://1.bp.blogspot.com/-6rLO7_yoe6w/Vqg971lJ8GI/AAAAAAAADkM/uGAQ8bsxYb8/s1600/06.%25E5%25AE%2589%25E8%25A3%259D%25E6%259C%258D%25E5%258B%2599.png)</div>
服務就安裝好了
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-3cK_eEnf4kg/Vqg98D_gpwI/AAAAAAAADkU/TUBeL9FKSV8/s1600/07.%25E6%259C%258D%25E5%258B%2599%25E5%25AE%2589%25E8%25A3%259D.png)](http://4.bp.blogspot.com/-3cK_eEnf4kg/Vqg98D_gpwI/AAAAAAAADkU/TUBeL9FKSV8/s1600/07.%25E6%259C%258D%25E5%258B%2599%25E5%25AE%2589%25E8%25A3%259D.png)</div>
解除安裝只要在執行檔後面加上uninstall參數就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-uA5zSmZopiQ/Vqg98MU_ArI/AAAAAAAADkY/YPSWE2dvc_A/s1600/08.%25E8%25A7%25A3%25E9%2599%25A4%25E5%25AE%2589%25E8%25A3%259D.png)](http://3.bp.blogspot.com/-uA5zSmZopiQ/Vqg98MU_ArI/AAAAAAAADkY/YPSWE2dvc_A/s1600/08.%25E8%25A7%25A3%25E9%2599%25A4%25E5%25AE%2589%25E8%25A3%259D.png)</div>
更詳細的功能可以參考官網的文件
[TopShlep官網](http://topshelf-project.com/)