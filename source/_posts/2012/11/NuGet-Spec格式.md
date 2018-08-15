---
title: NuGet Spec格式
tags:
  - NuGet
date: 2012-11-05 18:13:00
---

套件的.nuspec檔案，預設是包括這些內容

<pre class="brush: xml">&lt;?xml version="1.0"?&gt;
&lt;package &gt;
&nbsp; &lt;metadata&gt;
&nbsp;&nbsp;&nbsp; &lt;id&gt;$id$&lt;/id&gt;
&nbsp;&nbsp;&nbsp; &lt;version&gt;$version$&lt;/version&gt;
&nbsp;&nbsp;&nbsp; &lt;title&gt;$title$&lt;/title&gt;
&nbsp;&nbsp;&nbsp; &lt;authors&gt;$author$&lt;/authors&gt;
&nbsp;&nbsp;&nbsp; &lt;owners&gt;$author$&lt;/owners&gt;
&nbsp;&nbsp;&nbsp; &lt;licenseUrl&gt;http://LICENSE_URL_HERE_OR_DELETE_THIS_LINE&lt;/licenseUrl&gt;
&nbsp;&nbsp;&nbsp; &lt;projectUrl&gt;http://PROJECT_URL_HERE_OR_DELETE_THIS_LINE&lt;/projectUrl&gt;
&nbsp;&nbsp;&nbsp; &lt;iconUrl&gt;http://ICON_URL_HERE_OR_DELETE_THIS_LINE&lt;/iconUrl&gt;
&nbsp;&nbsp;&nbsp; &lt;requireLicenseAcceptance&gt;false&lt;/requireLicenseAcceptance&gt;
&nbsp;&nbsp;&nbsp; &lt;description&gt;$description$&lt;/description&gt;
&nbsp;&nbsp;&nbsp; &lt;releaseNotes&gt;Summary of changes made in this release of the package.&lt;/releaseNotes&gt;
&nbsp;&nbsp;&nbsp; &lt;copyright&gt;Copyright 2012&lt;/copyright&gt;
&nbsp;&nbsp;&nbsp; &lt;tags&gt;Tag1 Tag2&lt;/tags&gt;
&nbsp; &lt;/metadata&gt;
&lt;/package&gt;

</pre><div class="separator" style="clear: both; text-align: left;">$id對應的是這個套件的檔名</div>$version$對應的是AssemblyInfo.cs中的AssemblyVersionAttribute
$author$對應的是AssemblyInfo.cs中的AssemblyCompanyAttribute
$description$對應的是AssemblyInfo.cs中的AssemblyDescriptionAttribute
$title是套件的顯示名稱

requireLicenseAcceptance是安裝的時後要不要跳授權對話方塊
$licenseUrl是使用條款的網址
$projectUrl是專案資訊的網址
$iconUrl是套件icon的網址 

除了這幾個用來設定套件資訊的項目之外，還可以在這個檔案中包含相依性
例如要在這個套件中，使用到log4net套件，那只要加一行dependencies資料就行了
<pre class="brush: xml">&lt;dependencies&gt;
  &lt;dependency id="log4net" version="2.0.0" /&gt;
&lt;/dependencies&gt;
</pre>
除了相依性，還可以指定GAC裡面的Assembly，例如System.ServiceModel
<pre class="brush: xml">&lt;frameworkAssemblies&gt;
  &lt;frameworkAssembly assemblyName="System.ServiceModel" targetFramework="net40" /&gt;
&lt;/frameworkAssemblies&gt;</pre>
如果要額外打包檔案的話，就要用files這個tag了
src指定檔案所在的相對路徑，target指定檔案在套件中的位置
也可以萬用字元和exclude來排除特定檔案 
<pre class="brush: xml">&lt;files&gt;
  &lt;file src="bin\Debug\*.dll" target="lib" /&gt; 
  &lt;file src="bin\Debug\*.pdb" target="lib" /&gt; 
  &lt;file src="tools\**\*.*" exclude="**\*.log" /&gt;
&lt;/files&gt;</pre>
參考資料:

[Nuspec Reference](http://docs.nuget.org/docs/reference/nuspec-reference)

上一篇: [NuGet的Cofing設定檔和Source Code轉換](http://blog.developer.idv.tw/2012/11/nugetcofingsource-code.html)
下一篇: [Nuget 版本控制](http://blog.developer.idv.tw/2012/11/nuget.html)