---
title: Redis RedisOutputCacheProvider
tags:
  - Redis
date: 2015-01-21 17:51:00
---

先開個Web專案
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-W0eH1UB-UAg/VL9vePbpb0I/AAAAAAAACI4/dA1ZpbAc2uo/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://3.bp.blogspot.com/-W0eH1UB-UAg/VL9vePbpb0I/AAAAAAAACI4/dA1ZpbAc2uo/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>
安裝Microsoft.Web.RedisOutputCacheProvider套件
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-QT6Acrh4AnY/VL9106aZdnI/AAAAAAAACJg/7SwSvzSuaow/s1600/02.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)](http://4.bp.blogspot.com/-QT6Acrh4AnY/VL9106aZdnI/AAAAAAAACJg/7SwSvzSuaow/s1600/02.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)</div>
web.config中的caching區段會自動帶入預設的設定
註解的說明也很清楚
<div><pre class="brush:csharp">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;configuration&gt;
  &lt;system.web&gt;
    &lt;compilation debug="true" targetFramework="4.5" /&gt;
    &lt;httpRuntime targetFramework="4.5" /&gt;
    &lt;caching&gt;
      &lt;outputCache defaultProvider="MyRedisOutputCache"&gt;
        &lt;providers&gt;
          &lt;!-- Either use 'connectionString' and provide all parameters as string OR use 'host','port','accessKey','ssl','connectionTimeoutInMilliseconds' and 'operationTimeoutInMilliseconds'. --&gt;
          &lt;!-- 'databaseId' and 'applicationName' can be used with both options. --&gt;
          &lt;!--
          &lt;add name="MyRedisOutputCache" 
            host = "127.0.0.1" [String]
            port = "" [number]
            accessKey = "" [String]
            ssl = "false" [true|false]
            databaseId = "0" [number]
            applicationName = "" [String]
            connectionTimeoutInMilliseconds = "5000" [number]
            operationTimeoutInMilliseconds = "1000" [number]
            connectionString = "&lt;valid StackExchange.Redis connection string&gt;" [String]
          /&gt;
          --&gt;
          &lt;add name="MyRedisOutputCache" type="Microsoft.Web.Redis.RedisOutputCacheProvider" host="10.9.11.64" accessKey="" ssl="false" /&gt;
        &lt;/providers&gt;
      &lt;/outputCache&gt;
    &lt;/caching&gt;
  &lt;/system.web&gt;
&lt;/configuration&gt;
</pre></div>
隨便輸出點東西
<div><pre class="brush:csharp">namespace WebApplication1
{
    using System;

    public partial class WebForm1 : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            Response.Write(DateTime.Now);
        }
    }
}
</pre></div>
頁面啟用快取
<div><pre class="brush:html">&lt;%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="WebApplication1.WebForm1" %&gt;
&lt;%@ OutputCache Duration="60" VaryByParam="*" %&gt;
&lt;!DOCTYPE html&gt;

&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head runat="server"&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"/&gt;
    &lt;title&gt;&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;form id="form1" runat="server"&gt;
    &lt;div&gt;

    &lt;/div&gt;
    &lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;

</pre></div>網頁輸出的結果
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-by2w238QgVI/VL92f8VkUzI/AAAAAAAACJo/lpbT_JMRf7A/s1600/03.%E7%B6%B2%E9%A0%81%E7%B5%90%E6%9E%9C.png)](http://1.bp.blogspot.com/-by2w238QgVI/VL92f8VkUzI/AAAAAAAACJo/lpbT_JMRf7A/s1600/03.%E7%B6%B2%E9%A0%81%E7%B5%90%E6%9E%9C.png)</div>
Redis上面存在的資料
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-banUlA3Yokc/VL92jLW0W6I/AAAAAAAACJw/HwN6RslnBD4/s1600/04.Redis%E7%B5%90%E6%9E%9C.png)](http://4.bp.blogspot.com/-banUlA3Yokc/VL92jLW0W6I/AAAAAAAACJw/HwN6RslnBD4/s1600/04.Redis%E7%B5%90%E6%9E%9C.png)</div>