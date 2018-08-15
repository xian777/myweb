---
title: NLog Debugger Target
tags:
  - NLog
date: 2012-12-31 01:13:00
---

## NLog Debugger Target
<div>將Log輸出到Vistual Studio的輸出視窗，Web應用程式的開發很有幫助</div><div>
</div>

## 屬性
<div>基本上和其他Target一樣，沒有特別需要介紹的屬性</div><div>完整資料還是參考[官網的Debugger Target文件](https://github.com/nlog/nlog/wiki/Debugger-target)</div><div>
</div><div>

*   name - Target的名稱
*   header - 頭部格式
*   layout - 輸出格式
*   footer - 尾部格式<div>屬性很簡單，設定檔也簡單</div></div><div><pre class="brush:csharp">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;

    &lt;!-- 
  See http://nlog-project.org/wiki/Configuration_file 
  for information on customizing logging rules and outputs.
   --&gt;
    &lt;targets&gt;
        &lt;target xsi:type="Debugger" name="f"
            layout="${longdate} ${uppercase:${level}} ${message}" /&gt;
    &lt;/targets&gt;
    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="f" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div>