---
title: NuGet編譯後自動發佈套件
tags:
  - NuGet
date: 2012-10-21 20:33:00
---

<div class="separator" style="clear: both; text-align: left;">每次發佈套件，都要打一連串的命令太累了，比較簡單的方式是在專案中加上一個組態</div><div class="separator" style="clear: both; text-align: left;">在這個組態的建置後事件輸入命令就行了</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">首先，先打開專案的組態管理員</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-sDCdzMVuYp8/UIPalMG8KkI/AAAAAAAAANE/uQInD6zMN8g/s1600/01.ConfigMgr.png)](http://3.bp.blogspot.com/-sDCdzMVuYp8/UIPalMG8KkI/AAAAAAAAANE/uQInD6zMN8g/s1600/01.ConfigMgr.png)</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">新增一個組態</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-xCbZwESH_N8/UIPalua1W-I/AAAAAAAAANM/Z20zxEXMn2w/s1600/02.NewConfig.png)](http://2.bp.blogspot.com/-xCbZwESH_N8/UIPalua1W-I/AAAAAAAAANM/Z20zxEXMn2w/s1600/02.NewConfig.png)</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">名稱輸入NuGetPack</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-3oyPK-uxThc/UIPamann2lI/AAAAAAAAANU/Mq-5Bt_m9Ys/s1600/03.NugetPackConfig.png)](http://3.bp.blogspot.com/-3oyPK-uxThc/UIPamann2lI/AAAAAAAAANU/Mq-5Bt_m9Ys/s1600/03.NugetPackConfig.png)</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">再來在專案上按右鍵，選擇卸載專案</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-ByxhJPKdoNU/UIPam0tyYLI/AAAAAAAAANc/aa5geuvAM3A/s1600/04.UnloadProject.png)](http://4.bp.blogspot.com/-ByxhJPKdoNU/UIPam0tyYLI/AAAAAAAAANc/aa5geuvAM3A/s1600/04.UnloadProject.png)</div><div class="separator" style="clear: both; text-align: left;">再選擇編輯專案檔</div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-3y_YI_ZdAvQ/UIPanStvz2I/AAAAAAAAANk/5fBdjy3NAVI/s1600/05.EditProj.png)](http://2.bp.blogspot.com/-3y_YI_ZdAvQ/UIPanStvz2I/AAAAAAAAANk/5fBdjy3NAVI/s1600/05.EditProj.png)</div><div class="separator" style="clear: both; text-align: left;">在檔案的最下面，輸入建置後事件</div><div class="separator" style="clear: both; text-align: left;">之後要發佈的時後，選擇這個組態後編譯就行了</div><pre class="brush:xml">&lt;Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" /&gt;
  &lt;!-- To modify your build process, add your task inside one of the targets below and uncomment it. 
       Other similar extension points exist, see Microsoft.Common.targets.
  &lt;Target Name="BeforeBuild"&gt;
  &lt;/Target&gt;
  &lt;Target Name="AfterBuild"&gt;
  &lt;/Target&gt;
  --&gt;
  &lt;PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'NuGetPack|AnyCPU'"&gt;
    &lt;PostBuildEvent&gt;
  CD $(ProjectDir)
  nuget pack -sym -prop configuration=release -build
  nuget push *.symbols.nupkg 123 -Source http://localhost:2335/NuGet
  del *.symbols.nupkg
  nuget push *.nupkg 123456 -s http://localhost:1968
  del *.nupkg
 &lt;/PostBuildEvent&gt;
  &lt;/PropertyGroup&gt;
&lt;/Project&gt;
</pre><div class="separator" style="clear: both; text-align: left;">參考資料:</div><div class="separator" style="clear: both; text-align: left;"></div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">[NuGet系列-編譯後自動發佈](http://www.dotblogs.com.tw/wadehuang36/archive/2011/10/06/nuget-buildandpush.aspx)</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">上一篇:[建立NuGet套件](http://blog.developer.idv.tw/2012/10/nuget_21.html)</div><div class="separator" style="clear: both; text-align: left;">下一篇: [NuGet的Cofing設定檔和Source Code轉換](http://blog.developer.idv.tw/2012/11/nugetcofingsource-code.html)</div>