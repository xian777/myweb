---
title: Visual Studio 程式碼分析
tags:
  - Code Analysis
  - FxCop
date: 2014-04-22 13:38:00
---

<div>Visual Studio內建的程式碼分析，功能和Fxcop一樣用來對編譯出來的的Assembly做分析
這裡以一個簡單的網站當例子</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Vb_xWiwDI6M/U1XnV68asaI/AAAAAAAABOs/xxPRf3OER7U/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://3.bp.blogspot.com/-Vb_xWiwDI6M/U1XnV68asaI/AAAAAAAABOs/xxPRf3OER7U/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>
<div>選擇空白的MVC專案</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-MVgS-qgi4pk/U1XnYLAjtDI/AAAAAAAABPY/-BqHSmWSK_M/s1600/02.MVC%25E5%25B0%2588%25E6%25A1%2588.png)](http://1.bp.blogspot.com/-MVgS-qgi4pk/U1XnYLAjtDI/AAAAAAAABPY/-BqHSmWSK_M/s1600/02.MVC%25E5%25B0%2588%25E6%25A1%2588.png)</div>
<div>在專案設定中的程式碼分析有一些預設的規則集</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-Ys253RmWmjo/U1XnV626otI/AAAAAAAABOw/O0dQZgKvY3U/s1600/03.%25E5%25B0%2588%25E6%25A1%2588%25E8%25A8%25AD%25E5%25AE%259A.png)](http://1.bp.blogspot.com/-Ys253RmWmjo/U1XnV626otI/AAAAAAAABOw/O0dQZgKvY3U/s1600/03.%25E5%25B0%2588%25E6%25A1%2588%25E8%25A8%25AD%25E5%25AE%259A.png)</div>
<div>可以新增自訂的規則集</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-h72BZRA2ZFc/U1XnWQe0PhI/AAAAAAAABO8/Ga8-4BIp1ow/s1600/04.%25E6%2596%25B0%25E5%25A2%259E%25E8%25A6%258F%25E5%2589%2587%25E9%259B%2586.png)](http://2.bp.blogspot.com/-h72BZRA2ZFc/U1XnWQe0PhI/AAAAAAAABO8/Ga8-4BIp1ow/s1600/04.%25E6%2596%25B0%25E5%25A2%259E%25E8%25A6%258F%25E5%2589%2587%25E9%259B%2586.png)</div>
<div>記得在屬性視窗中去修改這個規則集的顯示名稱</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-_YerSEatUhw/U1XnWlCyRNI/AAAAAAAABPM/RFAIwLjqtwc/s1600/05.%25E4%25BF%25AE%25E6%2594%25B9%25E8%25A6%258F%25E5%2589%2587%25E9%259B%2586%25E5%2590%258D%25E7%25A8%25B1.png)](http://4.bp.blogspot.com/-_YerSEatUhw/U1XnWlCyRNI/AAAAAAAABPM/RFAIwLjqtwc/s1600/05.%25E4%25BF%25AE%25E6%2594%25B9%25E8%25A6%258F%25E5%2589%2587%25E9%259B%2586%25E5%2590%258D%25E7%25A8%25B1.png)</div>
<div>調整自訂的規則集</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Vk7DdmFofho/U1XnXGtMVbI/AAAAAAAABPI/3_x3XdR-nzA/s1600/06.%25E8%25AA%25BF%25E6%2595%25B4%25E8%25A6%258F%25E5%2589%2587%25E9%259B%2586.png)](http://3.bp.blogspot.com/-Vk7DdmFofho/U1XnXGtMVbI/AAAAAAAABPI/3_x3XdR-nzA/s1600/06.%25E8%25AA%25BF%25E6%2595%25B4%25E8%25A6%258F%25E5%2589%2587%25E9%259B%2586.png)</div>
<div>就可以在剛剛專案屬性中選擇自訂的規則集</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-bjjTg1JDYWM/U1XnaWimi2I/AAAAAAAABP4/O9YeOeUJsO8/s1600/07.%25E9%2581%25B8%25E6%2593%2587%25E8%2587%25AA%25E8%25A8%2582%25E8%25A6%258F%25E5%2589%2587%25E9%259B%2586.png)](http://4.bp.blogspot.com/-bjjTg1JDYWM/U1XnaWimi2I/AAAAAAAABP4/O9YeOeUJsO8/s1600/07.%25E9%2581%25B8%25E6%2593%2587%25E8%2587%25AA%25E8%25A8%2582%25E8%25A6%258F%25E5%2589%2587%25E9%259B%2586.png)</div>
<div>在專案上面按右鍵選擇分析</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Rz_jWNFB1Kg/U1XnYOrwXsI/AAAAAAAABPg/w_9Jv3hORD4/s1600/08.%25E5%25B0%2588%25E6%25A1%2588%25E4%25B8%258A%25E9%2581%25B8%25E6%2593%2587%25E5%2588%2586%25E6%259E%2590.png)](http://4.bp.blogspot.com/-Rz_jWNFB1Kg/U1XnYOrwXsI/AAAAAAAABPg/w_9Jv3hORD4/s1600/08.%25E5%25B0%2588%25E6%25A1%2588%25E4%25B8%258A%25E9%2581%25B8%25E6%2593%2587%25E5%2588%2586%25E6%259E%2590.png)</div>
<div>又或是在選擇工具列上的分析，快速鍵為Alt&nbsp;+ F11</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-9ZsXWNGeFDc/U1XnY_JxcRI/AAAAAAAABPo/HAKNKNEzZzM/s1600/09.%25E5%25B7%25A5%25E5%2585%25B7%25E5%2588%2597%25E4%25B8%258A%25E9%2581%25B8%25E6%2593%2587%25E5%2588%2586%25E6%259E%2590.png)](http://3.bp.blogspot.com/-9ZsXWNGeFDc/U1XnY_JxcRI/AAAAAAAABPo/HAKNKNEzZzM/s1600/09.%25E5%25B7%25A5%25E5%2585%25B7%25E5%2588%2597%25E4%25B8%258A%25E9%2581%25B8%25E6%2593%2587%25E5%2588%2586%25E6%259E%2590.png)</div>
<div>建置後就會跑出分析結果，該項目上點兩下就會切換到引發該訊息的原始碼處</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-SpipZT6VDXs/U1XnZOjsk_I/AAAAAAAABPs/97VlEH6oJ7s/s1600/10.%25E5%2588%2586%25E6%259E%2590%25E5%2595%258F%25E9%25A1%258C.png)](http://1.bp.blogspot.com/-SpipZT6VDXs/U1XnZOjsk_I/AAAAAAAABPs/97VlEH6oJ7s/s1600/10.%25E5%2588%2586%25E6%259E%2590%25E5%2595%258F%25E9%25A1%258C.png)</div>
<div>如果要知道這條規則更詳細的說明，就點擊左上方的規則編號
如果要先隱藏訊息的話，就在動作上面點一下，選擇隱藏訊息
這裡以在原始程式檔中為例</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-1XPg6CTlIB8/U1X_wYjG3eI/AAAAAAAABQI/HCnZUrYh8Aw/s1600/11.%E9%9A%B1%E8%97%8F%E8%A8%8A%E6%81%AF.png)](http://3.bp.blogspot.com/-1XPg6CTlIB8/U1X_wYjG3eI/AAAAAAAABQI/HCnZUrYh8Aw/s1600/11.%E9%9A%B1%E8%97%8F%E8%A8%8A%E6%81%AF.png)</div>
<div>就會在原始檔中加入SuppressMessage Attribute
記得要在屬性Justification中加入隱藏這個訊息的原因</div>
<div><pre class="brush:csharp">namespace DemoWeb
{
    public class MvcApplication : System.Web.HttpApplication
    {
        [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Performance", "CA1822:MarkMembersAsStatic", Justification = "DemoWeb不處理")]
        protected void Application_Start()
        {
            AreaRegistration.RegisterAllAreas();
            RouteConfig.RegisterRoutes(RouteTable.Routes);
        }
    }
}
</pre></div>
<div>相關連結

[Managed 程式碼的程式碼分析警告](http://msdn.microsoft.com/zh-tw/library/ee1hzekz.aspx)</div>