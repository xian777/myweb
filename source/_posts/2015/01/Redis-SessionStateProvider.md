---
title: Redis SessionStateProvider
tags:
  - Redis
date: 2015-01-21 17:28:00
---

首先開一個Web專案
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-W0eH1UB-UAg/VL9vePbpb0I/AAAAAAAACI4/dA1ZpbAc2uo/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://3.bp.blogspot.com/-W0eH1UB-UAg/VL9vePbpb0I/AAAAAAAACI4/dA1ZpbAc2uo/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>
安裝Microsoft.Web.RedisSessionStateProvider套件
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-DuvFSvwfNg4/VL9vy-aDZCI/AAAAAAAACJA/Isrbq2EmYPE/s1600/02.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)](http://1.bp.blogspot.com/-DuvFSvwfNg4/VL9vy-aDZCI/AAAAAAAACJA/Isrbq2EmYPE/s1600/02.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)</div>
設定檔中的sessionState自動會加入一段設定，註解的說明也很清楚
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;configuration&gt;
  &lt;system.web&gt;
    &lt;compilation debug="true" targetFramework="4.5" /&gt;
    &lt;httpRuntime targetFramework="4.5" /&gt;
    &lt;sessionState mode="Custom" customProvider="MySessionStateStore"&gt;
      &lt;providers&gt;
        &lt;!-- Either use 'connectionString' and provide all parameters as string OR use 'host','port','accessKey','ssl','connectionTimeoutInMilliseconds' and 'operationTimeoutInMilliseconds'. --&gt;
        &lt;!-- 'throwOnError','retryTimeoutInMilliseconds','databaseId' and 'applicationName' can be used with both options. --&gt;
        &lt;!--
          &lt;add name="MySessionStateStore" 
            host = "127.0.0.1" [String]
            port = "" [number]
            accessKey = "" [String]
            ssl = "false" [true|false]
            throwOnError = "true" [true|false]
            retryTimeoutInMilliseconds = "5000" [number]
            databaseId = "0" [number]
            applicationName = "" [String]
            connectionTimeoutInMilliseconds = "5000" [number]
            operationTimeoutInMilliseconds = "1000" [number]
            connectionString = "&lt;valid StackExchange.Redis connection string&gt;" [String]
          /&gt;
        --&gt;
        &lt;add name="MySessionStateStore" type="Microsoft.Web.Redis.RedisSessionStateProvider" host="10.9.11.64" accessKey="" ssl="false" /&gt;
      &lt;/providers&gt;
    &lt;/sessionState&gt;
  &lt;/system.web&gt;
&lt;/configuration&gt;
</pre></div>

隨便存取一個session
<div><pre class="brush:csharp">namespace WebApplication1
{
    using System;

    public partial class WebForm1 : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            var obj = Session["abc"];
            if (obj == null)
            {
                obj = DateTime.Now;
                Session["abc"] = obj;
            }

            Response.Write(Session.SessionID + "&lt;br/&gt;");
            Response.Write(obj);
        }
    }
}
</pre></div>
網頁輸出的資料
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-XDITvfzHrlQ/VL9xHz3vpMI/AAAAAAAACJM/j0doTj1aKNc/s1600/03.%E7%B6%B2%E9%A0%81%E7%B5%90%E6%9E%9C.png)](http://1.bp.blogspot.com/-XDITvfzHrlQ/VL9xHz3vpMI/AAAAAAAACJM/j0doTj1aKNc/s1600/03.%E7%B6%B2%E9%A0%81%E7%B5%90%E6%9E%9C.png)</div>
Redis上面存放的資料
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-Qc3XW48A9b4/VL9xLaLMkGI/AAAAAAAACJU/h03hTmz0EFE/s1600/04.Redis%E7%B5%90%E6%9E%9C.png)](http://1.bp.blogspot.com/-Qc3XW48A9b4/VL9xLaLMkGI/AAAAAAAACJU/h03hTmz0EFE/s1600/04.Redis%E7%B5%90%E6%9E%9C.png)</div>