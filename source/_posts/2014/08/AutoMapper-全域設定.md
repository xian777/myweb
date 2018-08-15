---
title: AutoMapper 全域設定
tags:
  - AutoMapper
date: 2014-08-06 13:32:00
---

<div>AutoMapper可以把物件的對應設定集中在一個設定檔裡面，然後用Profile來做群組分類
用一個簡單的MVC網站來做例子</div>
<div>首先是HomeModel物件</div><div><pre class="brush:csharp">public class HomeModel
{
    public int ModelId { get; set; }
    public string ModelName { get; set; }
}
</pre></div>
<div>再來是HomeViewModel物件</div><div><pre class="brush:csharp">public class HomeViewModel
{
    public int ViewModelId { get; set; }
    public string ViewModelName { get; set; }
}
</pre></div>
<div>接下來在App_Start裡面新增一個AutoMapperConfig檔案</div><div><pre class="brush:csharp">public class AutoMapperConfig
{
    public static void Configure()
    {
        Mapper.Initialize(x =&gt;
            {
                x.AddProfile&lt;HomeProfile&gt;();
            });
    }

    private class HomeProfile : Profile
    {
        protected override void Configure()
        {
            Mapper.CreateMap&lt;HomeModel, HomeViewModel&gt;()
                .ForMember(dest =&gt; dest.ViewModelId, opt =&gt; opt.MapFrom(src =&gt; src.ModelId))
                .ForMember(dest =&gt; dest.ViewModelName, opt =&gt; opt.MapFrom(src =&gt; src.ModelName));

            Mapper.CreateMap&lt;HomeViewModel, HomeModel&gt;()
                .ForMember(dest =&gt; dest.ModelId, opt =&gt; opt.MapFrom(src =&gt; src.ViewModelId))
                .ForMember(dest =&gt; dest.ModelName, opt =&gt; opt.MapFrom(src =&gt; src.ViewModelName));
        }
    }
}
</pre></div>
<div>然後在Global.asax中呼叫就行了</div><div><pre class="brush:csharp">public class MvcApplication : System.Web.HttpApplication
{
    protected void Application_Start()
    {
        AreaRegistration.RegisterAllAreas();
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        AutoMapperConfig.Configure();
    }
}
</pre></div>