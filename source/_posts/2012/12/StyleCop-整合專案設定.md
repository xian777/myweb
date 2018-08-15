---
title: StyleCop 整合專案設定
tags:
  - StyleCop
date: 2012-12-24 20:17:00
---

首先卸載專案

如果要讓沒通過規則的警告變成錯誤，可以在專案中加入StyleCopTreatErrorsAsWarnings這個屬性
<pre class="brush: xml">&lt;PropertyGroup&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;Configuration Condition=" '$(Configuration)' == '' "&gt;Debug&lt;/Configuration&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;Platform Condition=" '$(Platform)' == '' "&gt;AnyCPU&lt;/Platform&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;ProjectGuid&gt;{6F76C2E4-57EF-4A46-9A41-E7A9653F5EF9}&lt;/ProjectGuid&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;OutputType&gt;Exe&lt;/OutputType&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;AppDesignerFolder&gt;Properties&lt;/AppDesignerFolder&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;RootNamespace&gt;DemoApp&lt;/RootNamespace&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;AssemblyName&gt;DemoApp&lt;/AssemblyName&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;TargetFrameworkVersion&gt;v4.5&lt;/TargetFrameworkVersion&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;FileAlignment&gt;512&lt;/FileAlignment&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;StyleCopTreatErrorsAsWarnings&gt;false&lt;/StyleCopTreatErrorsAsWarnings&gt;
&lt;/PropertyGroup&gt;
</pre>
如果要編譯的時後，也做規則驗證，可以在最下面加入一個StyleCop.targets
<pre class="brush: xml">&lt;Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" /&gt;
&lt;Import Project="$(ProgramFiles)\MSBuild\StyleCop\v4.7\StyleCop.targets" /&gt;

</pre>
參考資料

http://blogs.msdn.com/b/sourceanalysis/archive/2008/05/24/source-analysis-msbuild-integration.aspx