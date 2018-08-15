---
title: NuGet Multiple Framework 建置
tags:
  - NuGet
date: 2013-12-24 11:20:00
---

<div>NuGet使用一段時間之後，開始碰到共用的元件，在不同專案的Framework版本不同，會有引用上的困擾，在網路上找了幾個解決方案，實作之後個人覺的比較簡單的方法如下

Step1 每個版本建立一個方案檔
一般專案的命名為net20、net35、net40、net45...
其他類型的專案則再加上縮寫
Client Profile(client)
WindowsPhone(wp)
Silverlight(sl)
CompactFramework(cf)
更多完整的資料請參考官網文件
[http://docs.nuget.org/docs/creating-packages/creating-and-publishing-a-package](http://docs.nuget.org/docs/creating-packages/creating-and-publishing-a-package)</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Z_7Nwh3E004/Urj3_IOzGmI/AAAAAAAAA3Q/JSdtbB7ne1Q/s1600/01.sln.png)](http://3.bp.blogspot.com/-Z_7Nwh3E004/Urj3_IOzGmI/AAAAAAAAA3Q/JSdtbB7ne1Q/s1600/01.sln.png)</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-w46datk00Fw/Urj4AWcam2I/AAAAAAAAA3Y/A-GmHxGvsY0/s1600/02.sln.png)](http://2.bp.blogspot.com/-w46datk00Fw/Urj4AWcam2I/AAAAAAAAA3Y/A-GmHxGvsY0/s1600/02.sln.png)</div><div>Step2 每一個版本建立一個專案檔</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-GcIzkWZiGz0/Urj4QuT3lII/AAAAAAAAA3c/IbIp_s_gt8g/s1600/03.csproj.png)](http://1.bp.blogspot.com/-GcIzkWZiGz0/Urj4QuT3lII/AAAAAAAAA3c/IbIp_s_gt8g/s1600/03.csproj.png)</div><span style="background-color: #fcfcfc; color: #333333; font-family: Consolas, 'Courier New'; font-size: 13.600000381469727px;">
</span>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-wPPOHszWFcA/Urj4RmcGNvI/AAAAAAAAA3o/XBtd2ATXs14/s1600/04.csproj.png)](http://3.bp.blogspot.com/-wPPOHszWFcA/Urj4RmcGNvI/AAAAAAAAA3o/XBtd2ATXs14/s1600/04.csproj.png)</div>
<div>Step3 每一個專案檔選擇不同的Framework，以及條件式編譯符號和修改輸出路徑 
**<span style="color: red;">注意每個組態都要設定喔 </span>**</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-B84By-NaVHE/Urj4ZL6TGpI/AAAAAAAAA3s/mZLbwfLGEHw/s1600/05.version.png)](http://2.bp.blogspot.com/-B84By-NaVHE/Urj4ZL6TGpI/AAAAAAAAA3s/mZLbwfLGEHw/s1600/05.version.png)</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-9Ka8GNPihf0/Urj4abt1ZLI/AAAAAAAAA34/jRp00XFmLv8/s1600/06.output.png)](http://2.bp.blogspot.com/-9Ka8GNPihf0/Urj4abt1ZLI/AAAAAAAAA34/jRp00XFmLv8/s1600/06.output.png)</div><div>Step4 依Framework版本，加上條件式編譯

</div><div><pre class="brush:csharp">using System;
using System.Collections.Generic;

#if NET35 || NET40 || NET45
using System.Linq;
#endif

using System.Text;

#if NET40 || NET45
using System.Threading.Tasks;
#endif

namespace ClassLibrary1
{
    public class Class1
    {
    }
}

</pre></div><div>Step5 手動建立nuget spec檔</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-_JkzDLOeeJc/Urj4jGQfcnI/AAAAAAAAA38/nPBreRhuDJA/s1600/07.spec.png)](http://2.bp.blogspot.com/-_JkzDLOeeJc/Urj4jGQfcnI/AAAAAAAAA38/nPBreRhuDJA/s1600/07.spec.png)</div><div><pre class="brush:xml">&lt;?xml version="1.0"?&gt;
&lt;package &gt;
  &lt;metadata&gt;
    &lt;id&gt;ClassLibrary1&lt;/id&gt;
    &lt;version&gt;1.0.0&lt;/version&gt;
    &lt;authors&gt;xian&lt;/authors&gt;
    &lt;owners&gt;xian&lt;/owners&gt;
    &lt;licenseUrl&gt;http://LICENSE_URL_HERE_OR_DELETE_THIS_LINE&lt;/licenseUrl&gt;
    &lt;projectUrl&gt;http://PROJECT_URL_HERE_OR_DELETE_THIS_LINE&lt;/projectUrl&gt;
    &lt;iconUrl&gt;http://ICON_URL_HERE_OR_DELETE_THIS_LINE&lt;/iconUrl&gt;
    &lt;requireLicenseAcceptance&gt;false&lt;/requireLicenseAcceptance&gt;
    &lt;description&gt;Package description&lt;/description&gt;
    &lt;releaseNotes&gt;Summary of changes made in this release of the package.&lt;/releaseNotes&gt;
    &lt;copyright&gt;Copyright 2013&lt;/copyright&gt;
    &lt;tags&gt;Tag1 Tag2&lt;/tags&gt;
    &lt;dependencies&gt;
      &lt;dependency id="SampleDependency" version="1.0" /&gt;
    &lt;/dependencies&gt;
  &lt;/metadata&gt;
  &lt;files&gt;
        &lt;file src="ClassLibrary1\**\*.cs" exclude="ClassLibrary1\obj\**\*.cs" target="src" /&gt;
  &lt;file src="ClassLibrary1\bin\Release\net20\ClassLibrary1.dll" target="lib\net20\ClassLibrary1.dll" /&gt;
        &lt;file src="ClassLibrary1\bin\Release\net20\ClassLibrary1.pdb" target="lib\net20\ClassLibrary1.pdb" /&gt;
  &lt;file src="ClassLibrary1\bin\Release\net35\ClassLibrary1.dll" target="lib\net35\ClassLibrary1.dll" /&gt;
        &lt;file src="ClassLibrary1\bin\Release\net35\ClassLibrary1.pdb" target="lib\net35\ClassLibrary1.pdb" /&gt;
        &lt;file src="ClassLibrary1\bin\Release\net40\ClassLibrary1.dll" target="lib\net40\ClassLibrary1.dll" /&gt;
        &lt;file src="ClassLibrary1\bin\Release\net40\ClassLibrary1.pdb" target="lib\net40\ClassLibrary1.pdb" /&gt;
  &lt;file src="ClassLibrary1\bin\Release\net45\ClassLibrary1.dll" target="lib\net45\ClassLibrary1.dll" /&gt;
        &lt;file src="ClassLibrary1\bin\Release\net45\ClassLibrary1.pdb" target="lib\net45\ClassLibrary1.pdb" /&gt;
    &lt;/files&gt;
&lt;/package&gt;&nbsp;</pre></div>
<div>Step6 加上測試用批次檔</div>
<div><pre class="brush:xml">@echo off
set MSBUILD=%WINDIR%\Microsoft.NET\Framework64\v4.0.30319\msbuild.exe
if not exist %MSBUILD% set MSBUILD=%WINDIR%\Microsoft.NET\Framework\v4.0.30319\msbuild.exe
if not exist %MSBUILD% set MSBUILD=%WINDIR%\Microsoft.NET\Framework\v3.5\msbuild.exe
if not exist %MSBUILD% (
 echo MSBuild not found
 exit
) 

%MSBUILD% ClassLibrary1.net20.sln /property:Configuration=Release /m
%MSBUILD% ClassLibrary1.net35.sln /property:Configuration=Release /m
%MSBUILD% ClassLibrary1.net40.sln /property:Configuration=Release /m
%MSBUILD% ClassLibrary1.net45.sln /property:Configuration=Release /m
nuget pack ClassLibrary1.nuspec
pause
</pre></div><div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-h_G_GN51AHQ/Urj9BdN5UuI/AAAAAAAAA4Q/v3soOklBVm8/s1600/09.bat.png)](http://3.bp.blogspot.com/-h_G_GN51AHQ/Urj9BdN5UuI/AAAAAAAAA4Q/v3soOklBVm8/s1600/09.bat.png)</div>

瀏覽結果</div>
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Li3Okgdz5VM/Urj4nvEX7QI/AAAAAAAAA4E/6K0LQ1Bu9KY/s1600/08.packet.png)](http://3.bp.blogspot.com/-Li3Okgdz5VM/Urj4nvEX7QI/AAAAAAAAA4E/6K0LQ1Bu9KY/s1600/08.packet.png)</div>