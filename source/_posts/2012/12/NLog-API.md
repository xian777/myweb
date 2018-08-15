---
title: NLog API
tags:
  - NLog
date: 2012-12-30 23:02:00
---

## LogManager
<div>LogManager是用來建立日誌和管理設定檔用的類別，有以下幾個Method</div><div>
</div><div>

*   LogManager.GetLogger - 取得或建立指定的logger
<span style="color: orange;">建議建立Logger的方式，需要手動指定名稱</span>
*   LogManager.GetCurrentClassLogger&nbsp; - 取得或建立目前類別名稱的logger
<span style="color: orange;">雖然比較方便，但底層是以StackTrace取得名稱，成本高很多</span>
*   LogManager.Configuration - 取得或設定目前日誌的設定資訊
*   LogManaget.GlobalThreshold - 取得或設定全域日誌的threshold

* * *

## Logger
<div>NLog.Logger類別是用來輸出Log用的，有以下幾個Method用來輸出不同層級的Log</div><div>每個Method都有多個overloads用來最小化內存配置以提高日誌速度</div><div><div>

*   Log() - 使用指定的格式和參數，將訊息寫入指定的級別
*   Trace() - 使用指定的格式和參數，將訊息寫入Trace級別
*   Debug() - 使用指定的格式和參數，將訊息寫入Debug級別
*   Info() - 使用指定的格式和參數，將訊息寫入Info級別
*   Warn() - 使用指定的格式和參數，將訊息寫入Warn級別
*   Erro() - 使用指定的格式和參數，將訊息寫入Error級別
*   Fatal() - 使用指定的格式和參數，將訊息寫入Fatal級別</div><div>以下的方法和屬性用來檢查該層級的日誌是否啟用</div><div>
</div><div>

*   IsEnabled() - 確定指定的級別日誌是否啟用
*   IsTraceEnabled - 確定Trace級別日誌是否啟用
*   IsDebugEnabled - 確定Debug級別日誌是否啟用
*   IsInfoEnabled - 確定Info級別日誌是否啟用
*   IsWarnEnabled - 確定Warn級別日誌是否啟用
*   IsErrorEnabled - 確定Error級別日誌是否啟用
*   IsFatalEnabled - 確定Fatal級別日誌是否啟用</div><span id="internal-source-marker_0.8555412123391619" style="font-size: 16px; vertical-align: baseline;">除此之外，NLog還提供了一組方法來記錄Exception</span>
<span style="font-size: 16px; vertical-align: baseline;">通過配置Layout Renderer的${exception}，可以取得很詳細的訊息</span>

*   <span style="vertical-align: baseline;">LogException() - 使用指定的格式和參數，將訊息和例外寫入指定的級別</span>
*   <span style="vertical-align: baseline;">TraceException() - 使用指定的格式和參數，將訊息和例外寫入Trace級別</span>
*   <span style="vertical-align: baseline;">DebugException() - 使用指定的格式和參數，將訊息和例外寫入Debug級別</span>
*   <span style="vertical-align: baseline;">InfoException() - 使用指定的格式和參數，將訊息和例外寫入Info級別</span>
*   <span style="vertical-align: baseline;">WarnException() - 使用指定的格式和參數，將訊息和例外寫曾Warn級別</span>
*   <span style="vertical-align: baseline;">ErrorException() - 使用指定的格式和參數，將訊息和例外寫曾Error級別</span>
*   <span style="vertical-align: baseline;">FatalException() - 使用指定的格式和參數，將訊息和例外寫曾Fatal級別</span><span style="font-size: 16px; vertical-align: baseline;"></span>
<span style="font-size: 16px; vertical-align: baseline;">${exception}的詳細設定方式，請參考</span>[<span style="color: #1155cc; font-size: 16px; vertical-align: baseline;">官網文件</span>](https://github.com/nlog/nlog/wiki/Exception-Layout-Renderer)<span style="font-size: 16px; vertical-align: baseline;"></span>

*   <span style="vertical-align: baseline;">format - 用逗號分隔的例外屬性例表，不區分大小寫
Message, Type, ShortType, ToString, Method, StackTrace</span>
*   <span style="vertical-align: baseline;">innerFormat - 用逗號分隔的例外屬性例表，不區分大小寫
Message, Type, ShortType, ToString, Method, StackTrace</span>
*   <span style="vertical-align: baseline;">maxInnerExceptionLevel - 內部錯誤的最大層數</span><span style="font-size: 16px; vertical-align: baseline;"></span>
<span style="font-size: 16px; vertical-align: baseline;">${onexception} - 用來輸出內部例外</span>
<span style="font-size: 16px; vertical-align: baseline;"></span>
<span style="font-size: 16px; vertical-align: baseline;">範例</span>
<span style="font-size: 16px; vertical-align: baseline;">StackTrace：${exception:format=stacktrace}</span>
<span style="font-size: 16px; vertical-align: baseline;">Exception Type：${exception:format=type}</span>
<span style="font-size: 16px; vertical-align: baseline;">Exception Message：${exception:format=message}</span>
<span style="font-size: 16px; vertical-align: baseline;">Inner  Exception  ：${onexception:${exception:format=type,message,method:maxInnerExceptionLevel=5:innerFormat=shortType,message,method}}</span>

* * *
<div>

## Example
</div></div></div><div>最基本的使用範例，取得Logger並輸出了一個字串訊息</div><div>
</div><div><pre class="brush:csharp">using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using NLog;

namespace NLogApp
{
    class Program
    {
        static readonly Logger log = LogManager.GetLogger("Program");

        static void Main(string[] args)
        {
            log.Debug("Debug Message...");
        }
    }
}

</pre></div><div>如果需要更多細部控制，可以實例化一個LogEvent來調整屬性，再傳給logger輸出</div><div><pre class="brush:csharp">using System;
using System.Globalization;
using NLog;

class MyClass
{
    static Logger logger = LogManager.GetLogger("MyClass");

    public void LogSomething()
    {
        LogEventInfo myEvent = new LogEventInfo(LogLevel.Debug, "", "My debug message");
        myEvent.LoggerName = logger.Name;
        myEvent.Properties.Add("MyCustomValue", "This is from MyClass");

        logger.Log(myEvent);
    }
}
</pre></div>