---
title: NLog.Elmah
tags:
  - NLog
  - NuGet
date: 2014-09-18 17:33:00
---

NLog.Elmah套件，是用來擴充NLog的Target，可以寫到Elmah去
Elmah的用法可以參考[之前的筆記](http://blog.developer.idv.tw/2014/09/elmah-error-logging-modules-and-handlers.html)
在設定好Elmah之後，開始來安裝NLog.Elmah
首先透過NuGet來安裝套件
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-7-Ra6YAOsCg/VBqk41izCYI/AAAAAAAABmI/cfGfIw-fulU/s1600/01.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)](http://3.bp.blogspot.com/-7-Ra6YAOsCg/VBqk41izCYI/AAAAAAAABmI/cfGfIw-fulU/s1600/01.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)</div>

再來設定NLog來套用Elmah
主要是透過extensions來引用NLog.Elmah這個Assembly
就可以透過Elmah這個Target，把Log寫到Elmah去
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;

    &lt;extensions&gt;
        &lt;add assembly="NLog.Elmah"/&gt;
    &lt;/extensions&gt;

    &lt;targets&gt;
        &lt;target xsi:type="Elmah" name="elmah"
                layout="${longdate} ${uppercase:${level}} ${message}"/&gt;
    &lt;/targets&gt;

    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="elmah" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div>

就可以在elmah中看到寫出的記錄，只是沒有Type，HttpStatusCode也都是0
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-IlyVebdJVBw/VBqmnO3VBJI/AAAAAAAABmU/MfcOlbctXZQ/s1600/02.%E5%AF%AB%E5%87%BA.png)](http://2.bp.blogspot.com/-IlyVebdJVBw/VBqmnO3VBJI/AAAAAAAABmU/MfcOlbctXZQ/s1600/02.%E5%AF%AB%E5%87%BA.png)</div>

如果加上LogLevelAsType="true"這個屬性
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" autoReload="true"&gt;

    &lt;extensions&gt;
        &lt;add assembly="NLog.Elmah"/&gt;
    &lt;/extensions&gt;

    &lt;targets&gt;
        &lt;target xsi:type="Elmah" name="elmah" LogLevelAsType="true"
                layout="${longdate} ${uppercase:${level}} ${message}"/&gt;
    &lt;/targets&gt;

    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="elmah" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div>

elmah的Type中，就會顯示Log的Level
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-5IPBWRrWs40/VBqmqaOZQPI/AAAAAAAABmc/6xaTP0h0oeg/s1600/03.%E5%A2%9E%E5%8A%A0Type.png)](http://3.bp.blogspot.com/-5IPBWRrWs40/VBqmqaOZQPI/AAAAAAAABmc/6xaTP0h0oeg/s1600/03.%E5%A2%9E%E5%8A%A0Type.png)</div>