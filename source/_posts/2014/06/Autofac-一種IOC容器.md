---
title: Autofac 一種IOC容器
tags:
  - Unit Test
date: 2014-06-04 10:55:00
---

接續之前提到的[IOC 控制反轉 &amp; DI 依賴注入](http://blog.developer.idv.tw/2014/05/ioc-di.html)和[Repostitory Pattern](http://blog.developer.idv.tw/2014/05/repostitory-pattern.html)，在Controller中提供了Repository介面的建構式，接下來就來介紹如何在網站啟動的時後，利用IOC容器把介面注入

首先透過NuGet安裝Autofac套件
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-ntFr0enXaqk/U46KMynHIaI/AAAAAAAABXk/B81ttCgQGnQ/s1600/01.NuGet.png)](http://1.bp.blogspot.com/-ntFr0enXaqk/U46KMynHIaI/AAAAAAAABXk/B81ttCgQGnQ/s1600/01.NuGet.png)</div>
因為是MVC專案，所以還要再裝一個MVC整合套件
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-7rOCvs9AgLQ/U46KQfEB8II/AAAAAAAABXs/P4WQJ1sUg5E/s1600/02.MVCPAckage.png)](http://2.bp.blogspot.com/-7rOCvs9AgLQ/U46KQfEB8II/AAAAAAAABXs/P4WQJ1sUg5E/s1600/02.MVCPAckage.png)</div>
依照慣例在App_Start資料夾下新增一個AutofacConfig
<div><pre class="brush:csharp">namespace WebApplication1
{
    using Autofac;
    using Autofac.Integration.Mvc;
    using System.Reflection;
    using System.Web.Mvc;

    public class AutofacConfig
    {
        public static void RegisterDependies()
        {
            ContainerBuilder builder = new ContainerBuilder();
            builder.RegisterControllers(Assembly.GetExecutingAssembly());
            builder.RegisterAssemblyTypes(Assembly.GetExecutingAssembly())
                .Where(x =&gt; x.Namespace.EndsWith("Repositories"))
                .AsImplementedInterfaces();
            IContainer container = builder.Build();
            DependencyResolver.SetResolver(new AutofacDependencyResolver(container));
        }
    }
}
</pre></div>
在Global的Application_Start事件中啟用Autofac
<div><pre class="brush:csharp">namespace WebApplication1
{
    using System.Web.Mvc;
    using System.Web.Routing;

    public class MvcApplication : System.Web.HttpApplication
    {
        protected void Application_Start()
        {
            AreaRegistration.RegisterAllAreas();
            FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
            RouteConfig.RegisterRoutes(RouteTable.Routes);
            AutofacConfig.RegisterDependies();
        }
    }
}
</pre></div>