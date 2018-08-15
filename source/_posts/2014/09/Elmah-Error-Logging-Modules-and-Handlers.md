---
title: Elmah (Error Logging Modules and Handlers)
tags:
  - Elmah
date: 2014-09-16 17:40:00
---

Elmah - Error Logging Modules and Handlers
是一個將未處理的Error記錄起來的模組，和包含一個顯示Log的處理常式
先開一個簡單的Web專案
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-TyswIpyTOZA/VBgAA5BWvHI/AAAAAAAABlE/NWJLVmrVZFc/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://2.bp.blogspot.com/-TyswIpyTOZA/VBgAA5BWvHI/AAAAAAAABlE/NWJLVmrVZFc/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>
透過NuGet安裝Elmah套件
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-RWj6U08DY2Q/VBgAAxYwTpI/AAAAAAAABlA/S2JQbGbvSk0/s1600/02.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)](http://2.bp.blogspot.com/-RWj6U08DY2Q/VBgAAxYwTpI/AAAAAAAABlA/S2JQbGbvSk0/s1600/02.%E5%AE%89%E8%A3%9D%E5%A5%97%E4%BB%B6.png)</div>
從設定檔上可以看到包含四個模組
<div><pre class="brush:xml">&lt;configSections&gt;
    &lt;sectionGroup name="elmah"&gt;
        &lt;section name="security" requirePermission="false" type="Elmah.SecuritySectionHandler, Elmah" /&gt;
        &lt;section name="errorLog" requirePermission="false" type="Elmah.ErrorLogSectionHandler, Elmah" /&gt;
        &lt;section name="errorMail" requirePermission="false" type="Elmah.ErrorMailSectionHandler, Elmah" /&gt;
        &lt;section name="errorFilter" requirePermission="false" type="Elmah.ErrorFilterSectionHandler, Elmah" /&gt;
    &lt;/sectionGroup&gt;
&lt;/configSections&gt;
</pre></div>
security，用來設定是否允許遠端讀取elmah.axd，
errorLog，用來設定Log要存在什麼地方，例如XML或DB，預設是Memory
errorMail，用來把Log送出EMail通知
errorFilter，用來過濾Log

elmah.axd是用來顯示Log的處理常式，如果允許遠端存取的時後，在安全性上要特別注意
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-_Ps8vplqOuY/VBgBnFqEfmI/AAAAAAAABlQ/MDIVTYN3ufQ/s1600/03.Elmah.axd.png)](http://4.bp.blogspot.com/-_Ps8vplqOuY/VBgBnFqEfmI/AAAAAAAABlQ/MDIVTYN3ufQ/s1600/03.Elmah.axd.png)</div>

如果要把記錄存在資料庫的話，以下用SQL Server為例子
首先到[官網取得資料表結構](https://code.google.com/p/elmah/source/browse/src/Elmah.SqlServer/SQLServer.sql)
或是透過NuGet安裝Elmah.SqlServer套件
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-sb1kLHepB98/VBgCV60F_-I/AAAAAAAABlY/wAbY9vnHuwc/s1600/04.elmah.sqlserver.png)](http://1.bp.blogspot.com/-sb1kLHepB98/VBgCV60F_-I/AAAAAAAABlY/wAbY9vnHuwc/s1600/04.elmah.sqlserver.png)</div>
就可以在App_Readme資料夾下找到SQL檔案
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-_jDh4hF8WcM/VBgCeqV0q5I/AAAAAAAABlg/VbW97vrHEQo/s1600/05.sql%E6%AA%94.png)](http://1.bp.blogspot.com/-_jDh4hF8WcM/VBgCeqV0q5I/AAAAAAAABlg/VbW97vrHEQo/s1600/05.sql%E6%AA%94.png)</div>
不過最好把NTEXT形態，改成NVARCHAR(MAX)比較好
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-vde3bv6V62U/VBgCm2s-pKI/AAAAAAAABlo/FQNfBqMyUpQ/s1600/06.%E6%94%B9%E6%AC%84%E4%BD%8D.png)](http://1.bp.blogspot.com/-vde3bv6V62U/VBgCm2s-pKI/AAAAAAAABlo/FQNfBqMyUpQ/s1600/06.%E6%94%B9%E6%AC%84%E4%BD%8D.png)</div>
準備好資料庫，包含ELMAH_Error資料表和三隻預儲程序
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-n9HDn_3aLM0/VBgDwExhESI/AAAAAAAABlw/-P7RYpLoBXA/s1600/07.%E6%BA%96%E5%82%99%E8%B3%87%E6%96%99%E5%BA%AB.png)](http://3.bp.blogspot.com/-n9HDn_3aLM0/VBgDwExhESI/AAAAAAAABlw/-P7RYpLoBXA/s1600/07.%E6%BA%96%E5%82%99%E8%B3%87%E6%96%99%E5%BA%AB.png)</div>透過errorLog設定Log寫到SQL Server
<div><pre class="brush:xml">&lt;elmah&gt;
    &lt;security allowRemoteAccess="false" /&gt;
    &lt;errorLog type="Elmah.SqlErrorLog, Elmah" connectionString="data source=(localdb)\v11.0; database=ElmahDB; trusted_connection=true" /&gt;
&lt;/elmah&gt;
</pre></div>
隨便丟個錯誤出來
<div><pre class="brush:csharp">namespace WebApplication1
{
    public partial class WebForm1 : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            throw new Exception("test");
        }
    }
}
</pre></div>
資料庫就有記錄了
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-aKiCFXWZg8g/VBgFF1EB-uI/AAAAAAAABl4/EFzUy-mrPDg/s1600/08.%E9%8C%AF%E8%AA%A4%E8%A8%98%E9%8C%84.png)](http://2.bp.blogspot.com/-aKiCFXWZg8g/VBgFF1EB-uI/AAAAAAAABl4/EFzUy-mrPDg/s1600/08.%E9%8C%AF%E8%AA%A4%E8%A8%98%E9%8C%84.png)</div>