---
title: 建立NuGet套件
tags:
  - NuGet
date: 2012-10-21 19:13:00
---

<div class="separator" style="clear: both; text-align: left;">首先下載NuGet命令列工具，請[按此下載](http://nuget.codeplex.com/releases/view/58939)</div><div class="separator" style="clear: both; text-align: left;">為了方便起見，把這個檔案丟到系統資料夾中，例如%WinDir%或System32&nbsp; </div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Iq1IYY5A7CA/UIPU0e78XoI/AAAAAAAAAMs/7ptcekOJkQQ/s1600/00.download.png)](http://2.bp.blogspot.com/-Iq1IYY5A7CA/UIPU0e78XoI/AAAAAAAAAMs/7ptcekOJkQQ/s1600/00.download.png)</div><div class="separator" style="clear: both; text-align: left;">接下來建立一個測試用的dll專案</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-HMrws61C34M/UIPTGsi4x9I/AAAAAAAAALE/1ymW04Gppqs/s1600/00.NewProject.png)](http://4.bp.blogspot.com/-HMrws61C34M/UIPTGsi4x9I/AAAAAAAAALE/1ymW04Gppqs/s1600/00.NewProject.png)</div>
<div class="separator" style="clear: both; text-align: left;">為了方便起見，請先安裝PowerCommands擴充元件</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-nJj9KyxiAaM/UIPTHOayBDI/AAAAAAAAALM/Nq0S4oy1bwI/s1600/01.PowerCommands.png)](http://2.bp.blogspot.com/-nJj9KyxiAaM/UIPTHOayBDI/AAAAAAAAALM/Nq0S4oy1bwI/s1600/01.PowerCommands.png)</div>
<div class="separator" style="clear: both; text-align: left;">在專案上按右鍵，就會出現Open Command Prompt這個功能，按下後會打開一個cmd視窗，並把路徑切換到專案下面</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-crRkZcmDMRw/UIPTH93kj0I/AAAAAAAAALU/mbkQ15Lmx5I/s1600/02.OpenCommandPrompt.png)](http://2.bp.blogspot.com/-crRkZcmDMRw/UIPTH93kj0I/AAAAAAAAALU/mbkQ15Lmx5I/s1600/02.OpenCommandPrompt.png)</div>
<div class="separator" style="clear: both; text-align: left;">輸入nuget spec，就會產生一個副檔名nuspec的檔案</div><div class="separator" style="clear: both; text-align: left;">P.S. 如果該目錄下不只一個專案檔(csproj)，請明確指定你要產生的專案檔是那一個 </div><div class="separator" style="clear: both; text-align: left;">ex. nuget spec xxx.csproj</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-Jz-baDzNlGc/UIPTIeo4bBI/AAAAAAAAALc/ZKcIqAgN_3w/s1600/03.NugetSpec.png)](http://3.bp.blogspot.com/-Jz-baDzNlGc/UIPTIeo4bBI/AAAAAAAAALc/ZKcIqAgN_3w/s1600/03.NugetSpec.png)</div>
<div class="separator" style="clear: both; text-align: left;">在專案總管上面按下顯示所有檔案，就可以看到這個檔案</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-lCpZOlgjhkU/UIPTJZ-ApfI/AAAAAAAAALk/FW-o1ID1r_A/s1600/04.ShowAllFile.png)](http://3.bp.blogspot.com/-lCpZOlgjhkU/UIPTJZ-ApfI/AAAAAAAAALk/FW-o1ID1r_A/s1600/04.ShowAllFile.png)</div>
<div class="separator" style="clear: both; text-align: left;">產生的nuspec檔案的內容如下</div>
<pre class="brush:xml">&lt;package&gt;
  &lt;metadata&gt;
    &lt;id&gt;$id$&lt;/id&gt;
    &lt;version&gt;$version$&lt;/version&gt;
    &lt;title&gt;$title$&lt;/title&gt;
    &lt;authors&gt;$author$&lt;/authors&gt;
    &lt;owners&gt;$author$&lt;/owners&gt;
    &lt;licenseurl&gt;http://LICENSE_URL_HERE_OR_DELETE_THIS_LINE&lt;/licenseurl&gt;
    &lt;projecturl&gt;http://PROJECT_URL_HERE_OR_DELETE_THIS_LINE&lt;/projecturl&gt;
    &lt;iconurl&gt;http://ICON_URL_HERE_OR_DELETE_THIS_LINE&lt;/iconurl&gt;
    &lt;requirelicenseacceptance&gt;false&lt;/requirelicenseacceptance&gt;
    &lt;description&gt;$description$&lt;/description&gt;
    &lt;releasenotes&gt;Summary of changes made in this release of the package.&lt;/releasenotes&gt;
    &lt;copyright&gt;Copyright 2012&lt;/copyright&gt;
    &lt;tags&gt;Tag1 Tag2&lt;/tags&gt;
  &lt;/metadata&gt;
&lt;/package&gt;
</pre>
<div class="separator" style="clear: both; text-align: left;">$id對應的是這個套件的名稱</div>$version$對應的是AssemblyInfo.cs中的AssemblyVersionAttribute
$author$對應的是AssemblyInfo.cs中的AssemblyCompanyAttribute
$description$對應的是AssemblyInfo.cs中的AssemblyDescriptionAttribute
當然也可以手動輸入，下次再來更詳細地說明這個檔案的格式

<div class="separator" style="clear: both; text-align: left;">接下來打包這個dll成一個套件，命令是nuget pack，參數說明如下</div>-sym:會一起產生包含偵錯符號的套件
-prop:用來額外指定一些特性，例如configuration=relase是編譯release這個組態
-build:是在打包前先編譯專案，以取得最新編譯的檔案
更詳細的說明，可以用nuget pack /?取得Help
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-pIv9pxm5ol8/UIPTKlzqTyI/AAAAAAAAAL0/2qzZFo0iKKU/s1600/06.NugetPack.png)](http://4.bp.blogspot.com/-pIv9pxm5ol8/UIPTKlzqTyI/AAAAAAAAAL0/2qzZFo0iKKU/s1600/06.NugetPack.png)</div>
<div class="separator" style="clear: both; text-align: left;">因為有下-sym這個參數，所以除了會把元件打包成{id}.{version}.nupkg這樣格式的檔案之外</div><div class="separator" style="clear: both; text-align: left;">還會產生一個{id}.{version}.symbols.nupkg的檔案</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-jVtaJ-nk4ls/UIPTLSt43zI/AAAAAAAAAL8/dQai5gRgPZY/s1600/07.Pkg.png)](http://1.bp.blogspot.com/-jVtaJ-nk4ls/UIPTLSt43zI/AAAAAAAAAL8/dQai5gRgPZY/s1600/07.Pkg.png)</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">接下來把這兩個檔案發佈到之前建立的nuget server和symbol server</div><div class="separator" style="clear: both; text-align: left;">發佈成功之後就可以使用NuGet來安裝這個套件了</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">發佈到nuget server</div>nuget push *.symbols.nupkg 123 -Source http://localhost:2335/NuGet

<div class="separator" style="clear: both; text-align: left;">發佈到symbol server</div>nuget push *.nupkg 123456 -s http://localhost:1968

參考網址:

[Creating and Publishing a Packag](http://docs.nuget.org/docs/creating-packages/Creating-and-Publishing-a-Package)

上一篇:[架設SymbolSource.Server](http://blog.developer.idv.tw/2012/10/symbolsourceserver.html)
下一篇: [NuGet編譯後自動發佈套件](http://blog.developer.idv.tw/2012/10/nuget_5451.html)