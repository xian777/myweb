---
title: 'C# 多國語系'
tags:
  - 'C#'
date: 2014-04-07 15:31:00
---

<div>C#的語系格式為languagecode2-country/regioncode2
可用以下列的語法列舉出所有語系</div>
<div><pre class="brush:csharp">foreach (CultureInfo ci in CultureInfo.GetCultures(CultureTypes.AllCultures))
{
    Console.WriteLine(ci.Name);
}
</pre></div>
<div>在.NET3.5之前簡中為zh-CHS，繁中為zh-CHT
在NET4.0之後簡中為zh-Hans，繁中為zh-Hant</div><div>在C#中影響目前語系的屬性有二個
Thread.CurrentThread.CurrentCulture影響的是控制台中的設定
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-yAGbJRIJZFk/U0JM_0G_KvI/AAAAAAAABIE/yihmCUKpkbw/s1600/01.%E6%8E%A7%E5%88%B6%E5%8F%B0.png)](http://3.bp.blogspot.com/-yAGbJRIJZFk/U0JM_0G_KvI/AAAAAAAABIE/yihmCUKpkbw/s1600/01.%E6%8E%A7%E5%88%B6%E5%8F%B0.png)</div>
例如日期、數字、貨幣的顯示格式</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-am2qr9Txbm4/U0JNC5e2TdI/AAAAAAAABIM/EWAZZGoXLSM/s1600/02.%E6%A0%BC%E5%BC%8F.png)](http://3.bp.blogspot.com/-am2qr9Txbm4/U0JNC5e2TdI/AAAAAAAABIM/EWAZZGoXLSM/s1600/02.%E6%A0%BC%E5%BC%8F.png)</div>
<div>Thread.CurrentThread.CurrentUICulture影響的則是要選用那個語系的資源檔</div><div>在ASP.NET中可以透過設定檔來啟用多國語系</div>
<div><pre class="brush:xml">&lt;system.web&gt;
    &lt;globalization culture="auto" uiCulture="auto" /&gt;
&lt;/system.web&gt;
</pre></div>
<div>就會自動以Http通訊協定中的Accept-Language的順序來選擇語系 </div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-79chB1gPP78/U0JNMI80AsI/AAAAAAAABIU/FszxyUony9U/s1600/03.AcceptLanguage.png)](http://3.bp.blogspot.com/-79chB1gPP78/U0JNMI80AsI/AAAAAAAABIU/FszxyUony9U/s1600/03.AcceptLanguage.png)</div>
<div>以ASP.NET WebForm為例，可以利用兩個特殊的資料夾 </div>App_GlobalResources裡面的資源檔是全域的
App_LocalResources裡面的資源檔則是只有該層目錄下有效
將資源檔的名稱取成和Page一樣，就可以在頁面中使用GetLocalResourceObject取出資源檔中的值
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-UOsyS9PleYY/U0JNUJfjIaI/AAAAAAAABIc/0iWHhGU_GeI/s1600/04.LocalResources.png)](http://2.bp.blogspot.com/-UOsyS9PleYY/U0JNUJfjIaI/AAAAAAAABIc/0iWHhGU_GeI/s1600/04.LocalResources.png)</div>
<div><pre class="brush:csharp">namespace WebApplication1
{
    public partial class Default : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            Object s1 = this.GetLocalResourceObject("s1");
            Response.Write(s1.ToString());
        }
    }
}
</pre></div>
<div>除了依瀏覽器的設定來選擇語系之外，也可以強制指定語系
比較常見的情況是讓使用者自行選擇語系後用cookie或session記住
然後在AcquireRequestState事件中取代目前的指定語系</div>
<div><pre class="brush:csharp">namespace WebApplication1
{
    public class Global : System.Web.HttpApplication
    {
        protected void Application_Start(object sender, EventArgs e)
        {
        }

        protected void Application_AcquireRequestState(object sender, EventArgs e)
        {
            HttpCookie cookie = this.Request.Cookies["_lang"];
            if (cookie != null)
            {
                Thread.CurrentThread.CurrentCulture = new CultureInfo(cookie.Value);
                Thread.CurrentThread.CurrentUICulture = new CultureInfo(cookie.Value);
            }
        }
    }
}
</pre></div><div>
</div>在MVC專案中可以改用強型別的方式來存取資源檔
先新增一個Resources資料夾，然後建立各語系的資源檔
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-Ta8KAh6emcE/U0JTO52irsI/AAAAAAAABIs/zrTQ9h3FJPU/s1600/05.Resources.png)](http://1.bp.blogspot.com/-Ta8KAh6emcE/U0JTO52irsI/AAAAAAAABIs/zrTQ9h3FJPU/s1600/05.Resources.png)</div>
在View中直接使用該類別即可
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-L7kAv2gp2Yg/U0JTk04Ww6I/AAAAAAAABI0/JE5q5KiNifU/s1600/06.View.png)](http://3.bp.blogspot.com/-L7kAv2gp2Yg/U0JTk04Ww6I/AAAAAAAABI0/JE5q5KiNifU/s1600/06.View.png)</div>
<div>如果資源檔要改存取資料庫的話，可以參考這個連結
[http://afana.me/post/aspnet-mvc-internationalization-store-strings-in-database-or-xml.aspx](http://afana.me/post/aspnet-mvc-internationalization-store-strings-in-database-or-xml.aspx)</div>