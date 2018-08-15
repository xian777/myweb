---
title: Octopus打包網站專案
tags:
  - Octopus
date: 2012-11-05 20:47:00
---

<div class="separator" style="clear: both; text-align: left;">先建一個HelloWorld的空白站台</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-q-PoZn-V6so/UJey4s6A-gI/AAAAAAAAAQ4/VkzzC4SN6sQ/s1600/01.NewProject.png)](http://1.bp.blogspot.com/-q-PoZn-V6so/UJey4s6A-gI/AAAAAAAAAQ4/VkzzC4SN6sQ/s1600/01.NewProject.png)</div>
<div class="separator" style="clear: both; text-align: left;">新增一個首頁，輸出Hello和目前時間</div>
<pre class="brush: csharp">using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace HelloWorld
{
&nbsp;&nbsp;&nbsp; public partial class _default : System.Web.UI.Page
&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; protected void Page_Load(object sender, EventArgs e)
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; Response.Write("hello:" + DateTime.Now.ToString());
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; }
&nbsp;&nbsp;&nbsp; }
}

</pre>
<div class="separator" style="clear: both; text-align: left;">接下來用NuGet安裝OctoPack套件</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-JZBnLxWF4Fg/UJey5I_yqbI/AAAAAAAAARA/DPpwKjhGQAs/s1600/02.OctoPack.png)](http://3.bp.blogspot.com/-JZBnLxWF4Fg/UJey5I_yqbI/AAAAAAAAARA/DPpwKjhGQAs/s1600/02.OctoPack.png)</div>
<div class="separator" style="clear: both; text-align: left;">新增一個nuspec檔案，但所有佔位符號都要手動輸入</div><pre class="brush: xml">&lt;?xml version="1.0"?&gt;
&lt;package &gt;
&nbsp; &lt;metadata&gt;
&nbsp;&nbsp;&nbsp; &lt;id&gt;HelloWorld&lt;/id&gt;
&nbsp;&nbsp;&nbsp; &lt;version&gt;1.0.0.0&lt;/version&gt;
&nbsp;&nbsp;&nbsp; &lt;title&gt;佈署測試用Package&lt;/title&gt;
&nbsp;&nbsp;&nbsp; &lt;authors&gt;Xian&lt;/authors&gt;
&nbsp;&nbsp;&nbsp; &lt;owners&gt;Xian&lt;/owners&gt;
&nbsp;&nbsp;&nbsp; &lt;licenseUrl&gt;http://LICENSE_URL_HERE_OR_DELETE_THIS_LINE&lt;/licenseUrl&gt;
&nbsp;&nbsp;&nbsp; &lt;projectUrl&gt;http://PROJECT_URL_HERE_OR_DELETE_THIS_LINE&lt;/projectUrl&gt;
&nbsp;&nbsp;&nbsp; &lt;iconUrl&gt;http://ICON_URL_HERE_OR_DELETE_THIS_LINE&lt;/iconUrl&gt;
&nbsp;&nbsp;&nbsp; &lt;requireLicenseAcceptance&gt;false&lt;/requireLicenseAcceptance&gt;
&nbsp;&nbsp;&nbsp; &lt;description&gt;佈署測試用...&lt;/description&gt;
&nbsp;&nbsp;&nbsp; &lt;releaseNotes&gt;Summary of changes made in this release of the package.&lt;/releaseNotes&gt;
&nbsp;&nbsp;&nbsp; &lt;copyright&gt;Copyright 2012&lt;/copyright&gt;
&nbsp;&nbsp;&nbsp; &lt;tags&gt;Tag1 Tag2&lt;/tags&gt;
&nbsp; &lt;/metadata&gt;
&lt;/package&gt;

</pre><div class="separator" style="clear: both; text-align: left;">選擇Release組態，按下建置</div>
<div class="separator" style="clear: both; text-align: left;">bin資料夾下就可以得到這個網站的套件</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-japnZvmbHog/UJe1DhHUsfI/AAAAAAAAARQ/0KQr17x0ehs/s1600/03.Package.png)](http://1.bp.blogspot.com/-japnZvmbHog/UJe1DhHUsfI/AAAAAAAAARQ/0KQr17x0ehs/s1600/03.Package.png)</div>
<div class="separator" style="clear: both; text-align: left;">為了方便起見，爬了一下文，找到利用MSBuild和參數來完成同樣的工具</div>順便佈署到NuGet Server去

<div class="separator" style="clear: both; text-align: left;">msbuild Ruby1_WS.csproj /t:Rebuild /t:ResolveReferences /t:_CopyWebApplication /p:Configuration=Release /p:WebProjectOutputDir=publish\ /p:OutDir=publish\bin\</div>/p:OctopusPublishPackageToHttp=http://NuGetServer所在網址 /p:OctopusPublishApiKey=NuGetServer上傳的密碼

參考網址:

[OctoPack Web Application Publishing](https://github.com/OctopusDeploy/OctoPack)

上一篇: [安裝Octopus Tentacle](http://blog.developer.idv.tw/2012/11/octopus-tentacle.html)
下一篇:&nbsp; [Octopus部署專案](http://blog.developer.idv.tw/2012/11/octopus_3840.html)