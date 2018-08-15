---
title: dbup - 資料庫更新工具
tags: []
date: 2016-05-18 15:34:00
---

dbup是一個用來更新資料庫的工庫，只能往前更新，不能往後回復更新
dbup-consolescripts是用來新增一個年月日時分秒_檔名.sql的套件

新增一個Console專案
<div class="separator" style="clear: both; text-align: center;">[![](https://4.bp.blogspot.com/-mogF88yuPbM/VzwauDgNoCI/AAAAAAAADxs/xQeX1VxpOh0gCJj1SDOHjbU38SjXthHQgCLcB/s1600/01.png)](https://4.bp.blogspot.com/-mogF88yuPbM/VzwauDgNoCI/AAAAAAAADxs/xQeX1VxpOh0gCJj1SDOHjbU38SjXthHQgCLcB/s1600/01.png)</div>

## 透過NuGet新增dbup和db-consolescripts套件
```shell
$ install-package dbup
$ install-package dbup-consolescripts
```
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-oV1LzJLW774/VzwauAIASRI/AAAAAAAADxk/0ahWoAwgPMcxgb21clM47CU7mhOZPhhRQCLcB/s1600/02.png)](https://2.bp.blogspot.com/-oV1LzJLW774/VzwauAIASRI/AAAAAAAADxk/0ahWoAwgPMcxgb21clM47CU7mhOZPhhRQCLcB/s1600/02.png)</div>

# 加入System.Configuration參考
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-2MXHs6-ULcU/VzwauNNva1I/AAAAAAAADxo/4u4Kh9JLsn09nbXM-nbdqo5Oa00XHRCAQCLcB/s1600/03.png)](https://2.bp.blogspot.com/-2MXHs6-ULcU/VzwauNNva1I/AAAAAAAADxo/4u4Kh9JLsn09nbXM-nbdqo5Oa00XHRCAQCLcB/s1600/03.png)</div>

## 新增連線字串
```xml
&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;configuration&gt;

&nbsp; &nbsp; &lt;connectionStrings&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;add name="DBConn" providerName="System.Data.SqlClient"
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;connectionString="data source=(localdb)\ATCity;initial catalog=RankingSystem;trusted_connection=true;"/&gt;
&nbsp; &nbsp; &lt;/connectionStrings&gt;
&nbsp; &nbsp;
&nbsp; &nbsp; &lt;startup&gt;
&nbsp; &nbsp; &nbsp; &nbsp; &lt;supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" /&gt;
&nbsp; &nbsp; &lt;/startup&gt;
&lt;/configuration&gt;
```

## 修改Program.cs
```cs
namespace SGT.ATCity.RankingSystem.Database
{
&nbsp; &nbsp; using System;
&nbsp; &nbsp; using System.Configuration;
&nbsp; &nbsp; using System.Reflection;
&nbsp; &nbsp; using DbUp;

&nbsp; &nbsp; public class Program
&nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; private static int Main(string[] args)
&nbsp; &nbsp; &nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var connectionString = ConfigurationManager.ConnectionStrings["DBConn"].ConnectionString;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var upgrader =
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; DeployChanges.To
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .SqlDatabase(connectionString)
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .WithScriptsEmbeddedInAssembly(Assembly.GetExecutingAssembly())
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .LogToConsole()
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .Build();

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var result = upgrader.PerformUpgrade();

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (!result.Successful)
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Console.ForegroundColor = ConsoleColor.Red;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Console.WriteLine(result.Error);
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Console.ResetColor();
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return -1;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Console.ForegroundColor = ConsoleColor.Green;
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Console.WriteLine("Success!");
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Console.ResetColor();
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return 0;
&nbsp; &nbsp; &nbsp; &nbsp; }
&nbsp; &nbsp; }
}
```
## 新增SQL檔案
* 透過套件管理器主控台執行New-Migration 名稱, 即可新增一個年月日時分秒_名稱的sql檔案
* 檔案的順序很重要, 會影響呼叫的執行順序
* 編輯要更新資料庫的SQL語法

<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-z6hmfsyfRSg/VzwauckPVTI/AAAAAAAADxw/aOHvq5xrR9AEdB4RcY8XcN6SHcTCuadnACLcB/s1600/04.png)](https://1.bp.blogspot.com/-z6hmfsyfRSg/VzwauckPVTI/AAAAAAAADxw/aOHvq5xrR9AEdB4RcY8XcN6SHcTCuadnACLcB/s1600/04.png)</div>

# 按下F5執行資料庫更新
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-BC3wQlzmEZc/VzwaujPeeMI/AAAAAAAADx0/TZB4dww4HqMoWwNyFg6kjPfUjlvC6N_OwCLcB/s1600/05.png)](https://1.bp.blogspot.com/-BC3wQlzmEZc/VzwaujPeeMI/AAAAAAAADx0/TZB4dww4HqMoWwNyFg6kjPfUjlvC6N_OwCLcB/s1600/05.png)</div>

# 資料庫更新結果
* 新增一個SchemaVersions資料表來記錄更新的記錄
* 相同檔名只會執行一次

<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-6as9yxMcY7g/VzwauoTO58I/AAAAAAAADx4/QFz_LWjEFtsPFKmHKcr8nhJ0CFxMWgFdgCLcB/s1600/06.png)](https://3.bp.blogspot.com/-6as9yxMcY7g/VzwauoTO58I/AAAAAAAADx4/QFz_LWjEFtsPFKmHKcr8nhJ0CFxMWgFdgCLcB/s1600/06.png)</div>