---
title: Frame Hijacking 防止其他站台用Frame包住自家的網站
tags: []
date: 2015-05-20 15:37:00
---

建立簡單的三個站台
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-bmqrkBwnMi0/VVw5htGvBVI/AAAAAAAACSc/yGWZiLD-X4c/s1600/00.site.png)](http://1.bp.blogspot.com/-bmqrkBwnMi0/VVw5htGvBVI/AAAAAAAACSc/yGWZiLD-X4c/s1600/00.site.png)</div>
w1.aaa.com
<div><pre class="brush:html">&lt;%@ Page Language="C#" AutoEventWireup="true" CodeBehind="default.aspx.cs" Inherits="w1._default" %&gt;

&lt;!DOCTYPE html&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head runat="server"&gt;
    &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
    &lt;title&gt;&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;form id="form1" runat="server"&gt;
        &lt;div&gt;
            w1
        &lt;/div&gt;
    &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre></div>
w2.bbb.com
<div><pre class="brush:html">&lt;%@ Page Language="C#" AutoEventWireup="true" CodeBehind="default.aspx.cs" Inherits="w2._default" %&gt;

&lt;!DOCTYPE html&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head runat="server"&gt;
    &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
    &lt;title&gt;&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;form id="form1" runat="server"&gt;
        &lt;div&gt;
            w2
        &lt;/div&gt;
        &lt;br /&gt;
        &lt;div&gt;
            &lt;iframe src="http://w1.aaa.com" /&gt;
        &lt;/div&gt;
    &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;

</pre></div>
w3.ccc.com
<div><pre class="brush:html">&lt;%@ Page Language="C#" AutoEventWireup="true" CodeBehind="default.aspx.cs" Inherits="w3._default" %&gt;

&lt;!DOCTYPE html&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head runat="server"&gt;
    &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
    &lt;title&gt;&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;form id="form1" runat="server"&gt;
        &lt;div&gt;
            w3
        &lt;/div&gt;
        &lt;br /&gt;
        &lt;div&gt;
            &lt;iframe src="http://w1.aaa.com" /&gt;
        &lt;/div&gt;
    &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;

</pre></div>
在w2和w3這兩個站台中，都可以用iframe把w1給包進來
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-EY9jXx5UoIQ/VVw5hdRt0dI/AAAAAAAACSU/jkT1ziiQbnM/s1600/01.png)](http://4.bp.blogspot.com/-EY9jXx5UoIQ/VVw5hdRt0dI/AAAAAAAACSU/jkT1ziiQbnM/s1600/01.png)</div>
在w1站台中加入一個全域header
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;!--
  如需如何設定 ASP.NET 應用程式的詳細資訊，請造訪
  http://go.microsoft.com/fwlink/?LinkId=169433
  --&gt;
&lt;configuration&gt;

    &lt;system.web&gt;
        &lt;compilation debug="true" targetFramework="4.5" /&gt;
        &lt;httpRuntime targetFramework="4.5" /&gt;
    &lt;/system.web&gt;

    &lt;system.webServer&gt;
        &lt;httpProtocol&gt;
            &lt;customHeaders&gt;
                &lt;add name="X-Frame-Options" value="SAMEORIGIN" /&gt;
            &lt;/customHeaders&gt;
        &lt;/httpProtocol&gt;
    &lt;/system.webServer&gt;

&lt;/configuration&gt;
</pre></div>
w2和w3就不能用frame包住w1了
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-eRytF-lcF0E/VVw5hYAycJI/AAAAAAAACSY/mS_zuElzmTs/s1600/02%25E5%2590%258C%25E6%25BA%2590.png)](http://4.bp.blogspot.com/-eRytF-lcF0E/VVw5hYAycJI/AAAAAAAACSY/mS_zuElzmTs/s1600/02%25E5%2590%258C%25E6%25BA%2590.png)</div>
改用Content-Security-Policy
需要注意網站的通訊協定，如果有http和https的差別，就需要把通訊協定也明確指出
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;!--
  如需如何設定 ASP.NET 應用程式的詳細資訊，請造訪
  http://go.microsoft.com/fwlink/?LinkId=169433
  --&gt;
&lt;configuration&gt;

    &lt;system.web&gt;
        &lt;compilation debug="true" targetFramework="4.5" /&gt;
        &lt;httpRuntime targetFramework="4.5" /&gt;
    &lt;/system.web&gt;

    &lt;system.webServer&gt;
        &lt;httpProtocol&gt;
            &lt;customHeaders&gt;
                &lt;add name="Content-Security-Policy" value="frame-ancestors 'self' http://w2.bbb.com" /&gt;
            &lt;/customHeaders&gt;
        &lt;/httpProtocol&gt;
    &lt;/system.webServer&gt;

&lt;/configuration&gt;
</pre></div>
就可以指定特定的站台可以用frame包住w1
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-cc1A2CO6z9M/VVw5iLqWHfI/AAAAAAAACSg/FqUsiMlo-Qk/s1600/04CSP.png)](http://1.bp.blogspot.com/-cc1A2CO6z9M/VVw5iLqWHfI/AAAAAAAACSg/FqUsiMlo-Qk/s1600/04CSP.png)</div>