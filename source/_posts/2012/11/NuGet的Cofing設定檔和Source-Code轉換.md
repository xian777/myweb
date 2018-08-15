---
title: NuGet的Cofing設定檔和Source Code轉換
tags:
  - NuGet
  - XDT Transform
date: 2012-11-05 17:40:00
---

使用套件的時後，有時會需要指定設定檔，例如自訂的Section，或特定AppSetting的值
在打包的時後，只要在你想轉換的檔案後面加上.transform的副檔名就行了
以web.config為例，只要新增一個檔案名為web.config.transform在套件中，安裝套件的時後就會合併這個檔案的內容

web.config.transform
<pre class="brush: xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;configuration&gt;
 &lt;appSettings&gt;
  &lt;add key="aa" value="aa" /&gt;
  &lt;add key="bb" value="bb" /&gt;
  &lt;add key="cc" value="cc" /&gt;
  &lt;add key="dd" value="dd" /&gt;
 &lt;/appSettings&gt;
&lt;/configuration&gt;
</pre>
web.config
<pre class="brush: xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;configuration&gt;
 &lt;appSettings&gt;
  &lt;add key="aa" value="123" /&gt;
  &lt;add key="bb" value="" /&gt;
  &lt;add key="cc" /&gt;
 &lt;/appSettings&gt;
&lt;/configuration&gt;
</pre>
合併後的結果會變成
<pre class="brush: xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;configuration&gt;
 &lt;appSettings&gt;
  &lt;!-- 原來的值不變 --&gt;
    &lt;add key="aa" value="123" /&gt;
    &lt;add key="bb" value="" /&gt;
 &lt;!-- 合併的資料 --&gt;
    &lt;add key="aa" value="aa" /&gt;
    &lt;add key="bb" value="bb" /&gt;
    &lt;add key="cc" value="cc" /&gt;
    &lt;add key="dd" value="dd" /&gt;
 &lt;/appSettings&gt;
&lt;/configuration&gt;
</pre>
程式碼轉換的方式，是用.pp的副檔名
以用來動態掛載Application_Start的WebActivator套件為例
慣例是在App_Start資料夾下面，新增一段程式碼

<pre class="brush: csharp">&nbsp;using System.Web;

[assembly: WebActivator.PostApplicationStartMethod(typeof(WebApplication2.App_Start.Hello), "HelloWorld")]

namespace WebApplication2.App_Start
{
&nbsp;&nbsp; &nbsp;public class Hello
&nbsp;&nbsp; &nbsp;{
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;public static void HelloWorld()
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;{
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;HttpContext.Current.Application.Add("hello", "world");
&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;}
&nbsp;&nbsp; &nbsp;}
}
&nbsp;</pre>要包進套件的話，就要把檔名改成hello.cs.pp，再把程式碼置換成
<pre class="brush: csharp">using System.Web;

[assembly: WebActivator.PostApplicationStartMethod(typeof($rootnamespace$.App_Start.Hello), "HelloWorld")]

namespace $rootnamespace$.App_Start
{
&nbsp;&nbsp;&nbsp; public class Hello
&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; public static void HelloWorld()
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; HttpContext.Current.Application.Add("hello", "world");
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; }
&nbsp;&nbsp;&nbsp; }
}

</pre>
比較常用的應該是$rootnamespace$和$assemblyname$
詳細可置換的符號可以參考[ProjectProperties Properties](http://msdn.microsoft.com/en-us/library/vslangproj.projectproperties_properties)

參考資料:

[Configuration File and Source Code Transformations](http://docs.nuget.org/docs/creating-packages/configuration-file-and-source-code-transformations)

上一篇: [NuGet編譯後自動發佈套件](http://blog.developer.idv.tw/2012/10/nuget_5451.html)
下一篇: [NuGet Spec格式](http://blog.developer.idv.tw/2012/11/nuget-spec.html)