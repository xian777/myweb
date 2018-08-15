---
title: NuGet編譯後自動發佈套件
tags:
  - NuGet
date: 2012-10-21 20:33:00
---

# 前言
每次發佈套件，都要打一連串的命令太累了，比較簡單的方式是在專案中加上一個組態
在這個組態的建置後事件輸入命令就行了

## 首先先打開專案的組態管理員
[![](http://3.bp.blogspot.com/-sDCdzMVuYp8/UIPalMG8KkI/AAAAAAAAANE/uQInD6zMN8g/s1600/01.ConfigMgr.png)](http://3.bp.blogspot.com/-sDCdzMVuYp8/UIPalMG8KkI/AAAAAAAAANE/uQInD6zMN8g/s1600/01.ConfigMgr.png)

## 新增一個組態
![](http://2.bp.blogspot.com/-xCbZwESH_N8/UIPalua1W-I/AAAAAAAAANM/Z20zxEXMn2w/s1600/02.NewConfig.png)](http://2.bp.blogspot.com/-xCbZwESH_N8/UIPalua1W-I/AAAAAAAAANM/Z20zxEXMn2w/s1600/02.NewConfig.png)

## 名稱輸入NuGetPack
![](http://3.bp.blogspot.com/-3oyPK-uxThc/UIPamann2lI/AAAAAAAAANU/Mq-5Bt_m9Ys/s1600/03.NugetPackConfig.png)](http://3.bp.blogspot.com/-3oyPK-uxThc/UIPamann2lI/AAAAAAAAANU/Mq-5Bt_m9Ys/s1600/03.NugetPackConfig.png)

## 再來在專案上按右鍵，選擇卸載專案
![](http://4.bp.blogspot.com/-ByxhJPKdoNU/UIPam0tyYLI/AAAAAAAAANc/aa5geuvAM3A/s1600/04.UnloadProject.png)](http://4.bp.blogspot.com/-ByxhJPKdoNU/UIPam0tyYLI/AAAAAAAAANc/aa5geuvAM3A/s1600/04.UnloadProject.png)

## 再選擇編輯專案檔
![](http://2.bp.blogspot.com/-3y_YI_ZdAvQ/UIPanStvz2I/AAAAAAAAANk/5fBdjy3NAVI/s1600/05.EditProj.png)](http://2.bp.blogspot.com/-3y_YI_ZdAvQ/UIPanStvz2I/AAAAAAAAANk/5fBdjy3NAVI/s1600/05.EditProj.png)

## 在檔案的最下面，輸入建置後事件
## 之後要發佈的時後，選擇這個組態後編譯就行了
```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
  <!– To modify your build process, add your task inside one of the targets below and uncomment it.
       Other similar extension points exist, see Microsoft.Common.targets.
  <Target Name="BeforeBuild">
  </Target>
  <Target Name="AfterBuild">
  </Target>
  –>
  <PropertyGroup Condition="$(Configuration)|$(Platform)’ == ‘NuGetPack|AnyCPU">
    <PostBuildEvent>
  CD $(ProjectDir)
  nuget pack -sym -prop configuration=release -build
  nuget push .symbols.nupkg 123 -Source http://localhost:2335/NuGet
  del .symbols.nupkg
  nuget push .nupkg 123456 -s http://localhost:1968
  del .nupkg
 </PostBuildEvent>
  </PropertyGroup>
</Project>

```

## 參考資料
* [NuGet系列-編譯後自動發佈](http://www.dotblogs.com.tw/wadehuang36/archive/2011/10/06/nuget-buildandpush.aspx)