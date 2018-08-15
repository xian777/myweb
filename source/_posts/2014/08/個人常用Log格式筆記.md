---
title: 個人常用Log格式筆記
tags:
  - NLog
date: 2014-08-28 18:35:00
---

個人常用的Log格式，在此記錄一下

<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" autoReload="true"&gt;

    &lt;!-- 
  See https://github.com/nlog/nlog/wiki/Configuration-file 
  for information on customizing logging rules and outputs.
   --&gt;
    &lt;targets async="true"&gt;
        &lt;default-wrapper xsi:type="BufferingWrapper" bufferSize="500" flushTimeout="3000" /&gt;

        &lt;target xsi:type="Chainsaw" name="console" address="udp4://127.0.0.1:7071"
                layout="${longdate} ${uppercase:${level}} ${message}" /&gt;

        &lt;target xsi:type="File" name="file" fileName="D:\LogFiles\Proj_Log\${shortdate}\${date:format=yyyy-MM-dd-HH}.log"
                  layout="${longdate} ${uppercase:${level}} ${message}${newline}${onexception:inner=${newline}Exception:${newline}${exception:format=ToString}${newline}}STACKTRACE:${newline}${stacktrace:format=DetailedFlat}" /&gt;</pre><pre class="brush:xml">    &lt;/targets&gt;

    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="console,file" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div>