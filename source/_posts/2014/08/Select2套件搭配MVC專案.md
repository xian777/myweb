---
title: Select2套件搭配MVC專案
tags:
  - ASP.NET
  - MVC
  - Select2
date: 2014-08-26 14:55:00
---

首先開一個MVC專案
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-S1UzcfC0Y1o/U_wrT7TrJtI/AAAAAAAABj8/lbIoB2J113k/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://1.bp.blogspot.com/-S1UzcfC0Y1o/U_wrT7TrJtI/AAAAAAAABj8/lbIoB2J113k/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>
透過NuGet引用Select2.js套件
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-r0BD97ZmLPs/U_wrT5xcPTI/AAAAAAAABkE/LM86LOjUes0/s1600/02.%E5%BC%95%E7%94%A8%E5%8F%83%E8%80%83.png)](http://3.bp.blogspot.com/-r0BD97ZmLPs/U_wrT5xcPTI/AAAAAAAABkE/LM86LOjUes0/s1600/02.%E5%BC%95%E7%94%A8%E5%8F%83%E8%80%83.png)</div>
因為MVC使用Bootstrap框架，所以需要搭配[select2-bootstrap.css](http://zh-tw.cdnjs.com/libraries/select2)來修正畫面的輸出
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-D8ZI1EUPzcI/U_wrTxzEHOI/AAAAAAAABkA/rzGEPLiMOzw/s1600/03.SelectBootstrap.png)](http://1.bp.blogspot.com/-D8ZI1EUPzcI/U_wrTxzEHOI/AAAAAAAABkA/rzGEPLiMOzw/s1600/03.SelectBootstrap.png)</div>
新增一個HomeModel用來傳遞資料
<div><pre class="brush:csharp">public class HomeModel
{
    public IEnumerable&lt;int&gt; DataList { get; set; }
}
</pre><div>
在Controler中透過ViewBag，傳入一個MultiSelectList
<div><pre class="brush:csharp">public ActionResult Index()
{
    this.ViewBag.DataList = new MultiSelectList(
        new List&lt;SelectListItem&gt;()
        {
            new SelectListItem{ Text="aaa", Value="1"},
            new SelectListItem{ Text="bbb", Value="2"},
            new SelectListItem{ Text="ccc", Value="3"},
        }, "Value", "Text");

    return View();
}
</pre><div>
在View中透過@Html.ListBoxFor輸出下拉選單
<div><pre class="brush:html">@using WebApplication1.ViewModels
@model HomeModel
@{
    ViewBag.Title = "Index";
}

&lt;h2&gt;Index&lt;/h2&gt;

&lt;div class="form-horizontal"&gt;
    &lt;div class="form-group"&gt;
        @Html.LabelFor(x =&gt; x.DataList, new { @class = "col-md-2 label-control" })
        &lt;div class="col-md-10"&gt;
            @Html.ListBoxFor(x =&gt; x.DataList, null, new { @class = "form-control" })
        &lt;/div&gt;
    &lt;/div&gt;
&lt;/div&gt;

@section scripts
{
    &lt;script type="text/javascript"&gt;
        $("#DataList").select2();
    &lt;/script&gt;
}
</pre><div>
Select2套件在MVC專案中的樣子
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-jLL1ZTwa2T0/U_wuzJYxXzI/AAAAAAAABkY/lo1mxsr9FoE/s1600/04.%E4%BD%BF%E7%94%A8%E5%A5%97%E4%BB%B6.png)](http://4.bp.blogspot.com/-jLL1ZTwa2T0/U_wuzJYxXzI/AAAAAAAABkY/lo1mxsr9FoE/s1600/04.%E4%BD%BF%E7%94%A8%E5%A5%97%E4%BB%B6.png)</div>
如果是編輯頁面，初始化要有值的話，只要在model上面指定值
<div><pre class="brush:csharp">public ActionResult Edit(int? id)
{
    this.ViewBag.DataList = new MultiSelectList(
        new List&lt;SelectListItem&gt;()
    {
        new SelectListItem{ Text="aaa", Value="1"},
        new SelectListItem{ Text="bbb", Value="2"},
        new SelectListItem{ Text="ccc", Value="3"},
    }, "Value", "Text");

    HomeModel model = new HomeModel { DataList = new int[] { 1, 3 } };
    return View(model);
}
</pre><div>
初始化的時後就有值了
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-e7HSmAPFZ5w/U_wvHzhWuGI/AAAAAAAABkg/pAJ7ku5ZnpU/s1600/05.%E7%B7%A8%E8%BC%AF%E9%A0%81%E9%9D%A2.png)](http://4.bp.blogspot.com/-e7HSmAPFZ5w/U_wvHzhWuGI/AAAAAAAABkg/pAJ7ku5ZnpU/s1600/05.%E7%B7%A8%E8%BC%AF%E9%A0%81%E9%9D%A2.png)</div>

</div></div></div></div></div></div></div></div>