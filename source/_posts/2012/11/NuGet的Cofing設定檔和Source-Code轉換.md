---
title: NuGet的Cofing設定檔和Source Code轉換
tags:
  - NuGet
  - XDT Transform
date: 2012-11-05 17:40:00
---

## 前言
使用套件的時後，有時會需要指定設定檔，例如自訂的Section，或特定AppSetting的值
在打包的時後，只要在你想轉換的檔案後面加上.transform的副檔名就行了
以web.config為例，只要新增一個檔案名為web.config.transform在套件中，安裝套件的時後就會合併這個檔案的內容

## web.config.transform
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
 <appSettings>
  <add key="aa" value="aa" />
  <add key="bb" value="bb" />
  <add key="cc" value="cc" />
  <add key="dd" value="dd" />
 </appSettings>
</configuration>
```

## web.config
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
 <appSettings>
  <add key="aa" value="123" />
  <add key="bb" value="" />
  <add key="cc" />
 </appSettings>
</configuration>
```

## 合併後的結果會變成
```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
 <appSettings>
    <!– 原來的值不變 –>
    <add key="aa" value="123" />
    <add key="bb" value="" />
    <!– 合併的資料 –>
    <add key="aa" value="aa" />
    <add key="bb" value="bb" />
    <add key="cc" value="cc" />
    <add key="dd" value="dd" />
 </appSettings>
</configuration>
```

程式碼轉換的方式，是用.pp的副檔名
以用來動態掛載Application_Start的WebActivator套件為例
慣例是在App_Start資料夾下面，新增一段程式碼

```cs
using System.Web;

[assembly: WebActivator.PostApplicationStartMethod(typeof(WebApplication2.App_Start.Hello), “HelloWorld”)]
namespace WebApplication2.App_Start
{
    public class Hello
    {
        public static void HelloWorld()
        {
            HttpContext.Current.Application.Add(“hello”, “world”);
        }
    }
}
```

## 要包進套件的話，就要把檔名改成hello.cs.pp，再把程式碼置換成
```cs
using System.Web;

[assembly: WebActivator.PostApplicationStartMethod(typeof($rootnamespace$.App_Start.Hello), “HelloWorld”)]
namespace $rootnamespace$.App_Start
{
    public class Hello
    {
        public static void HelloWorld()
        {
            HttpContext.Current.Application.Add(“hello”, “world”);
        }
    }
}
```

比較常用的應該是$rootnamespace$和$assemblyname$
詳細可置換的符號可以參考[ProjectProperties Properties](http://msdn.microsoft.com/en-us/library/vslangproj.projectproperties_properties)

## 參考資料
* [Configuration File and Source Code Transformations](http://docs.nuget.org/docs/creating-packages/configuration-file-and-source-code-transformations)