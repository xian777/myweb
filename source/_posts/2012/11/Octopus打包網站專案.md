---
title: Octopus打包網站專案
tags:
  - Octopus
date: 2012-11-05 20:47:00
---

## 先建一個HelloWorld的空白站台
![](http://1.bp.blogspot.com/-q-PoZn-V6so/UJey4s6A-gI/AAAAAAAAAQ4/VkzzC4SN6sQ/s1600/01.NewProject.png)](http://1.bp.blogspot.com/-q-PoZn-V6so/UJey4s6A-gI/AAAAAAAAAQ4/VkzzC4SN6sQ/s1600/01.NewProject.png)

## 新增一個首頁，輸出Hello和目前時間
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;

namespace HelloWorld
{
    public partial class _default : System.Web.UI.Page
    {
        protected void Page_Load(object sender, EventArgs e)
        {
            Response.Write(“hello:” + DateTime.Now.ToString());
        }
    }
}
```

## 接下來用NuGet安裝OctoPack套件
![](http://3.bp.blogspot.com/-JZBnLxWF4Fg/UJey5I_yqbI/AAAAAAAAARA/DPpwKjhGQAs/s1600/02.OctoPack.png)](http://3.bp.blogspot.com/-JZBnLxWF4Fg/UJey5I_yqbI/AAAAAAAAARA/DPpwKjhGQAs/s1600/02.OctoPack.png)

## 新增一個nuspec檔案，但所有佔位符號都要手動輸入
```xml
<?xml version=”1.0”?>
<package >
  <metadata>
    <id>HelloWorld</id>
    <version>1.0.0.0</version>
    <title>佈署測試用Package</title>
    <authors>Xian</authors>
    <owners>Xian</owners>
    <licenseUrl>http://LICENSE_URL_HERE_OR_DELETE_THIS_LINE</licenseUrl>
    <projectUrl>http://PROJECT_URL_HERE_OR_DELETE_THIS_LINE</projectUrl>
    <iconUrl>http://ICON_URL_HERE_OR_DELETE_THIS_LINE</iconUrl>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <description>佈署測試用…</description>
    <releaseNotes>Summary of changes made in this release of the package.</releaseNotes>
    <copyright>Copyright 2012</copyright>
    <tags>Tag1 Tag2</tags>
  </metadata>
</package>
```

## 選擇Release組態，按下建置
## bin資料夾下就可以得到這個網站的套件
![](http://1.bp.blogspot.com/-japnZvmbHog/UJe1DhHUsfI/AAAAAAAAARQ/0KQr17x0ehs/s1600/03.Package.png)](http://1.bp.blogspot.com/-japnZvmbHog/UJe1DhHUsfI/AAAAAAAAARQ/0KQr17x0ehs/s1600/03.Package.png)

## 為了方便起見，爬了一下文，找到利用MSBuild和參數來完成同樣的工具
## 順便佈署到NuGet Server去

```shell
msbuild Ruby1_WS.csproj /t:Rebuild /t:ResolveReferences /t:_CopyWebApplication /p:Configuration=Release /p:WebProjectOutputDir=publish\ /p:OutDir=publish\bin\</div>/p:OctopusPublishPackageToHttp=http://NuGetServer所在網址 /p:OctopusPublishApiKey=NuGetServer上傳的密碼
```

## 參考網址
* [OctoPack Web Application Publishing](https://github.com/OctopusDeploy/OctoPack)