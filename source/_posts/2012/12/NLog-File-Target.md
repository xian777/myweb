---
title: NLog File Target
tags:
  - NLog
date: 2012-12-31 00:37:00
---

## NLog File Target
輸出到檔案是預設的設定，可以是一個或是多個檔案

## 參數
<div>File Target可以使用的參數很多，除了特殊需求之外，大部份採用預設值就行了</div><div>詳細說明請參考[官網File Target文件](https://github.com/nlog/nlog/wiki/File-target)</div><div>
</div><div>以下為常用的參數</div><div>

*   name - target的名稱
*   layout - 輸出格式，預設為${longdate}|${level:uppercase=true}|${logger}|${message}
*   header - 頭部格式
*   footer - 尾部格式
*   encoding - 檔案編碼，如果有中文字的話，可以指定成<span style="color: orange;">utf-8</span>
*   <span style="color: orange;">fileName - 檔案名稱，配合Layout Renderers組合檔名</span></div><div>

## 常用範例
非同步，每小時寫檔，UTF8格式</div><div><pre class="brush:csharp">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;

    &lt;!-- 
  See http://nlog-project.org/wiki/Configuration_file 
  for information on customizing logging rules and outputs.
   --&gt;
    &lt;targets&gt;
        &lt;target xsi:type="AsyncWrapper" name="f" queueLimit="5000" overflowAction="Discard"&gt;
            &lt;target xsi:type="File" fileName="${basedir}/logs/${date:format=yyyy-MM-dd-HH}.log"
                layout="${longdate} ${uppercase:${level}} ${message}" encoding="utf-8" /&gt;
        &lt;/target&gt;
    &lt;/targets&gt;
    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="f" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;</pre></div><div>
CSV格式
<div><pre class="brush:csharp">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;

    &lt;!-- 
  See http://nlog-project.org/wiki/Configuration_file 
  for information on customizing logging rules and outputs.
   --&gt;
    &lt;targets&gt;
        &lt;target xsi:type="AsyncWrapper" name="f" queueLimit="5000" overflowAction="Discard"&gt;
            &lt;target xsi:type="File" fileName="${basedir}/logs/${date:format=yyyy-MM-dd-HH}.log"
                layout="${longdate} ${uppercase:${level}} ${message}" encoding="utf-8" /&gt;
        &lt;/target&gt;
    &lt;/targets&gt;
    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="f" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div>
</div>