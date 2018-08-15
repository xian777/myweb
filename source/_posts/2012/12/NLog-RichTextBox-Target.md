---
title: NLog RichTextBox Target
tags:
  - NLog
date: 2012-12-31 02:06:00
---

## NLog RichTextBox Target
<div>將Log訊息寫到RichTextBox控制項</div><div>如果有現成的就指定控制項名稱，但需注意要在表單建立之後再取得Logger</div><div>例如在表單建構式之後，或是在Form_Load事件之後</div><div>不然還是會獨立建出一個RichTextBox出來</div><div>
</div><div><pre class="brush:csharp">static Logger log;

private void Form1_Load(object sender, EventArgs e)
{
    // 需在Form_Load才取得Logger
    log = LogManager.GetCurrentClassLogger();
}
</pre></div>

## 屬性
<div>完整資料請參考[官網的RichTextBox Target文件](https://github.com/nlog/nlog/wiki/RichTextBox-target)</div><div>

*   name - Target的名稱
*   layout - 輸出的格式
*   autoScroll - 是否自動捲動最下方
*   maxLines - 最大行數，超過會往上移動，移除最上方記錄
*   controlName - 控制項名稱
*   formName - 表單名稱
*   useDefaultRowColoringRules - Log文字是否使用預設的顏色<div>非同步，自動捲動，最大20行，使用預設色系的設定檔</div></div><div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;

    &lt;!-- 
  See http://nlog-project.org/wiki/Configuration_file 
  for information on customizing logging rules and outputs.
   --&gt;
    &lt;targets async="true"&gt;
        &lt;target xsi:type="RichTextBox" name="f" 
                autoScroll="true"
                maxLines="20" 
                formName="Form1" 
                controlName="richTextBox1"
                useDefaultRowColoringRules="true"
                layout="${longdate} ${uppercase:${level}} ${message}"  /&gt;
    &lt;/targets&gt;
    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="f" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div><div>
</div>