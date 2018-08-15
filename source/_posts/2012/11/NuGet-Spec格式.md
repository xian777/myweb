---
title: NuGet Spec格式
tags:
  - NuGet
date: 2012-11-05 18:13:00
---

## 套件的.nuspec檔案，預設是包括這些內容
```xml
<?xml version=”1.0”?>
<package >
  <metadata>
    <id>$id$</id>
    <version>$version$</version>
    <title>$title$</title>
    <authors>$author$</authors>
    <owners>$author$</owners>
    <licenseUrl>http://LICENSE_URL_HERE_OR_DELETE_THIS_LINE</licenseUrl>
    <projectUrl>http://PROJECT_URL_HERE_OR_DELETE_THIS_LINE</projectUrl>
    <iconUrl>http://ICON_URL_HERE_OR_DELETE_THIS_LINE</iconUrl>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <description>$description$</description>
    <releaseNotes>Summary of changes made in this release of the package.</releaseNotes>
    <copyright>Copyright 2012</copyright>
    <tags>Tag1 Tag2</tags>
  </metadata>
</package>
```

* $id對應的是這個套件的檔名
* $version$對應的是AssemblyInfo.cs中的AssemblyVersionAttribute
* $author$對應的是AssemblyInfo.cs中的AssemblyCompanyAttribute
* $description$對應的是AssemblyInfo.cs中的AssemblyDescriptionAttribute
* $title是套件的顯示名稱
* requireLicenseAcceptance是安裝的時後要不要跳授權對話方塊
* $licenseUrl是使用條款的網址
* $projectUrl是專案資訊的網址
* $iconUrl是套件icon的網址 

除了這幾個用來設定套件資訊的項目之外，還可以在這個檔案中包含相依性
例如要在這個套件中，使用到log4net套件，那只要加一行dependencies資料就行了
```xml
<dependencies>
  <dependency id=”log4net” version=”2.0.0” />
</dependencies>
```

除了相依性，還可以指定GAC裡面的Assembly，例如System.ServiceModel
```xml
<frameworkAssemblies>
  <frameworkAssembly assemblyName=”System.ServiceModel” targetFramework=”net40” />
</frameworkAssemblies>
```

如果要額外打包檔案的話，就要用files這個tag了
src指定檔案所在的相對路徑，target指定檔案在套件中的位置
也可以萬用字元和exclude來排除特定檔案 
```xml
<files>
  <file src=”bin\Debug*.dll” target=”lib” />
  <file src=”bin\Debug*.pdb” target=”lib” />
  <file src=”tools*\.“ exclude=”**\.log” />
</files>
```

## 參考資料
* [Nuspec Reference](http://docs.nuget.org/docs/reference/nuspec-reference)