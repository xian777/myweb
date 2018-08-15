---
title: 好用的LogViewer
tags:
  - NLog
date: 2013-11-04 18:25:00
---

Log2Console是個好用的Log Viewer，可以配合Log4Net或NLog使用
首先到[官網下載](http://log2console.codeplex.com/)
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-1SU04Sq3oOc/UndxtGbDi3I/AAAAAAAAA14/21nZBzzTQVg/s1600/01.download.png)](http://1.bp.blogspot.com/-1SU04Sq3oOc/UndxtGbDi3I/AAAAAAAAA14/21nZBzzTQVg/s1600/01.download.png)</div><span id="goog_1348107367"></span><span id="goog_1348107368"></span>

安裝好後先設定接收方式
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-hx4I28pk5po/Undxwe6iabI/AAAAAAAAA2A/1VERa_k_LQs/s1600/02.receive.png)](http://4.bp.blogspot.com/-hx4I28pk5po/Undxwe6iabI/AAAAAAAAA2A/1VERa_k_LQs/s1600/02.receive.png)</div>

這裡以UDP為例
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-DyJoQXRgRBo/Undx0h2GzVI/AAAAAAAAA2I/1L9xaWi3D3Q/s1600/03.add.png)](http://2.bp.blogspot.com/-DyJoQXRgRBo/Undx0h2GzVI/AAAAAAAAA2I/1L9xaWi3D3Q/s1600/03.add.png)</div>

設定要使用的Port號就行了
下方是log4net的設定範例
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-GkGKo0EWtOU/Undx4VhUDRI/AAAAAAAAA2Q/CBvil9xgUg4/s1600/04.udpport.png)](http://3.bp.blogspot.com/-GkGKo0EWtOU/Undx4VhUDRI/AAAAAAAAA2Q/CBvil9xgUg4/s1600/04.udpport.png)</div>

以NLog來當日誌輸出元件的話，可以透過Chainsaw將Log寫到指定的位址和埠號
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;

    &lt;!-- 
  See http://nlog-project.org/wiki/Configuration_file 
  for information on customizing logging rules and outputs.
   --&gt;
    &lt;targets&gt;
        &lt;target xsi:type="Chainsaw" name="viewer" address="tcp://127.0.0.1:7071"  /&gt;
    &lt;/targets&gt;

    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="viewer" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div>

隨便輸出幾個Log試試
<div><pre class="brush:csharp">using NLog;

namespace ConsoleApplication1
{
    class Program
    {
        private static Logger log = LogManager.GetLogger("Program");

        static void Main(string[] args)
        {
            log.Trace("trace");
            log.Debug("debug");
            log.Info("info");
            log.Warn("warn");
            log.Error("error");
            log.Fatal("fatal");
        }
    }
}
</pre></div>
單擊列表中的Log，可以在下方看到詳細資料
左上角的下拉選單可以用來過濾要顯示的層級
中間的搜尋框可以用來過濾日誌的內容
右邊的樹狀選單可以用來過濾Logger名稱
至於更詳細的設定，例如字型、顏色等功能，可在Settings裡面調整
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-rfZNdONB7CI/Und1p7MLCzI/AAAAAAAAA2o/Cl0WxPiCRpk/s1600/05.message.png)](http://3.bp.blogspot.com/-rfZNdONB7CI/Und1p7MLCzI/AAAAAAAAA2o/Cl0WxPiCRpk/s1600/05.message.png)</div>
<div class="separator" style="clear: both; text-align: center;"></div>