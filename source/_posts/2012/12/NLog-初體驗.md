---
title: NLog 初體驗
tags:
  - NLog
date: 2012-12-29 14:55:00
---

<div class="separator" style="clear: both; text-align: left;">先簡單介紹一下如何安裝NLog這個套件，和使用預設的設定檔來寫出Log</div><div class="separator" style="clear: both; text-align: left;">首先讓環境簡單點，所以開一個主控台專案來當範例</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-kY84lmK8n-Y/UN6LxFGNSKI/AAAAAAAAAls/avloE2j0DDU/s1600/01.NLogApp.png)](http://1.bp.blogspot.com/-kY84lmK8n-Y/UN6LxFGNSKI/AAAAAAAAAls/avloE2j0DDU/s1600/01.NLogApp.png)</div>
<div class="separator" style="clear: both; text-align: left;">接下來引用NLog最簡單的方式當然就是用NuGet安裝了</div><div class="separator" style="clear: both; text-align: left;">如果對NuGet不熟的話，可以參考之前的[NuGet學習筆記](http://blog.developer.idv.tw/2012/12/nuget.html)</div><div class="separator" style="clear: both; text-align: left;"></div>NLog這個套件是NLog.dll元件本身
NLog.Config這個套件是NLog.config和NLog.xsd(用來幫助在設定檔中的IntelliSense)

<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-q64xvtDQs48/UN6NL4Ig1YI/AAAAAAAAAmU/ZbCqaqjTbi0/s1600/02.NugetInstall.png)](http://1.bp.blogspot.com/-q64xvtDQs48/UN6NL4Ig1YI/AAAAAAAAAmU/ZbCqaqjTbi0/s1600/02.NugetInstall.png)</div><div class="separator" style="clear: both; text-align: left;">安裝好後，專案中就會多了這三個東西 </div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-JPz6V3bHo4Y/UN6NW6sNdhI/AAAAAAAAAmc/rLoiSFWHldA/s1600/03.SolutionExplorer.png)](http://1.bp.blogspot.com/-JPz6V3bHo4Y/UN6NW6sNdhI/AAAAAAAAAmc/rLoiSFWHldA/s1600/03.SolutionExplorer.png)</div>
<div class="separator" style="clear: both; text-align: left;">
</div>打開設定檔，把註解拿掉，先使用預設值來體驗一下
詳細的設定方式，之後再介紹

<pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
&nbsp; &nbsp; &nbsp; xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;
&nbsp; &nbsp; &lt;!--
&nbsp; See http://nlog-project.org/wiki/Configuration_file
&nbsp; for information on customizing logging rules and outputs.
&nbsp; &nbsp;--&gt;
&nbsp; &nbsp; &lt;targets&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;!-- add your targets here --&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;target xsi:type="File" name="f" fileName="${basedir}/logs/${shortdate}.log"
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; layout="${longdate} ${uppercase:${level}} ${message}" /&gt;
&nbsp; &nbsp; &lt;/targets&gt;
&nbsp; &nbsp; &lt;rules&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;!-- add your logging rules here --&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;logger name="*" minlevel="Trace" writeTo="f" /&gt;
&nbsp; &nbsp; &lt;/rules&gt;
&lt;/nlog&gt;
</pre><div class="separator" style="clear: both; text-align: left;">
</div>呼叫NLog的方式也很簡單，直接用LogManager來引用就行了
寫Log的方式也很直覺，總共有六個層級，都寫一個試試看

<pre class="brush:csharp">using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using NLog;

namespace NLogApp
{
    class Program
    {
        // 引用NLog
        static Logger log = LogManager.GetCurrentClassLogger();

        static void Main(string[] args)
        {
            // 每個層級都寫一個試試看
            log.Trace("trace");
            log.Debug("debug");
            log.Info("info");
            log.Warn("warn");
            log.Error("error");
            log.Fatal("fatal");
        }
    }
}
</pre>
<div class="separator" style="clear: both; text-align: left;">這裡需要注意一下，如果是App專案的話，NLog.config這個檔案的屬性</div><div class="separator" style="clear: both; text-align: left;">**複製到輸出目錄**要確定是在<span style="color: red;">永遠複製</span>這個選項</div><div class="separator" style="clear: both; text-align: left;">這樣Run的時後執行檔和設定檔在同一個目錄才會有作用</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-U2koFg5VAUQ/UN6QZTwYOYI/AAAAAAAAAnE/DeKoWFDmy5Q/s1600/04.AlwaysCopy.png)](http://3.bp.blogspot.com/-U2koFg5VAUQ/UN6QZTwYOYI/AAAAAAAAAnE/DeKoWFDmy5Q/s1600/04.AlwaysCopy.png)</div>
<div class="separator" style="clear: both; text-align: left;">編譯成功就執行一下，如果沒有權限問題的話，在執行檔下面就會寫出一個log檔</div><div class="separator" style="clear: both; text-align: left;">也會看到NLog.config複製到這裡</div><div class="separator" style="clear: both; text-align: left;">記得要按一下**方案總管**中的<span style="color: red;">顯示所有檔案</span>，才會看到不在專案中的檔案喔</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-8LBc7LR-EfQ/UN6STe5OY-I/AAAAAAAAAng/PBiaW4bVHjM/s1600/05.Run.png)](http://3.bp.blogspot.com/-8LBc7LR-EfQ/UN6STe5OY-I/AAAAAAAAAng/PBiaW4bVHjM/s1600/05.Run.png)</div>
<div class="separator" style="clear: both; text-align: left;">打開log檔，裡面就是剛寫的那六個層級的log，使用上就是這麼簡單 </div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-F4aPx1fJk6M/UN6SiLQDzVI/AAAAAAAAAno/IZPWmFq2rzs/s1600/06.Log.png)](http://2.bp.blogspot.com/-F4aPx1fJk6M/UN6SiLQDzVI/AAAAAAAAAno/IZPWmFq2rzs/s1600/06.Log.png)</div>
<div class="separator" style="clear: both; text-align: left;">下一篇:[NLog Config](http://blog.developer.idv.tw/2012/12/nlog-config.html)</div>