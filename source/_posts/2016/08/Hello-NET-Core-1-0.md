---
title: Hello .NET Core 1.0
tags: []
date: 2016-08-14 12:05:00
---

首先到[官網](https://www.microsoft.com/net/core#windows)按照步驟安裝SDK
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-8cuW-kzgdOA/V6_aFBAfQ5I/AAAAAAAADz4/BK4Nf_FlkBsQNDMzAGhUQooLGDlon56bwCLcB/s1600/01.png)](https://2.bp.blogspot.com/-8cuW-kzgdOA/V6_aFBAfQ5I/AAAAAAAADz4/BK4Nf_FlkBsQNDMzAGhUQooLGDlon56bwCLcB/s1600/01.png)</div>

使用dotnet new 命令來初始化一個專案
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-bHmStXZF-Yc/V6_aFE7U2HI/AAAAAAAADz8/FWvCy2ny7w49Ft8B-KhfcI4WjsvwFIhbQCLcB/s1600/02.png)](https://2.bp.blogspot.com/-bHmStXZF-Yc/V6_aFE7U2HI/AAAAAAAADz8/FWvCy2ny7w49Ft8B-KhfcI4WjsvwFIhbQCLcB/s1600/02.png)</div>
dotnet restore:還原套件
dotnet build:建置專案
dotnet run:執行專案
<div class="separator" style="clear: both; text-align: center;">[![](https://3.bp.blogspot.com/-NQgyN2ZYFsU/V6_aFGcGTmI/AAAAAAAADz0/u6mszI4_3HwObdE8_Yi0uAwHLFyzwZ7ggCLcB/s1600/03.png)](https://3.bp.blogspot.com/-NQgyN2ZYFsU/V6_aFGcGTmI/AAAAAAAADz0/u6mszI4_3HwObdE8_Yi0uAwHLFyzwZ7ggCLcB/s1600/03.png)</div>

打開http://127.0.01:5000就可以看到站台了
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/--vN4i89yLj0/V6_aFdNvrpI/AAAAAAAAD0A/Rry3hJLTG4kweQbP29448yzqsmgp0nD7wCLcB/s1600/04.png)](https://2.bp.blogspot.com/--vN4i89yLj0/V6_aFdNvrpI/AAAAAAAAD0A/Rry3hJLTG4kweQbP29448yzqsmgp0nD7wCLcB/s1600/04.png)</div>
dotnet publish: 發佈專案
帶入-output參數可以指發佈的路徑
<div class="separator" style="clear: both; text-align: center;">[![](https://2.bp.blogspot.com/-bLopWepOecU/V6_aFqVQhzI/AAAAAAAAD0E/EUhpOmrE-IMrqHU4l_qWgF-JuHN-w6PBgCLcB/s1600/05.png)](https://2.bp.blogspot.com/-bLopWepOecU/V6_aFqVQhzI/AAAAAAAAD0E/EUhpOmrE-IMrqHU4l_qWgF-JuHN-w6PBgCLcB/s1600/05.png)</div>

發佈後的資料夾
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-tCreZAN8ees/V6_aFvJt6yI/AAAAAAAAD0I/yCKsFT8w_YQjqBMeEhW5ky0TpCqVycU6wCLcB/s1600/07.png)](https://1.bp.blogspot.com/-tCreZAN8ees/V6_aFvJt6yI/AAAAAAAAD0I/yCKsFT8w_YQjqBMeEhW5ky0TpCqVycU6wCLcB/s1600/07.png)</div>
使用dotnet命令來執行專案的dll
<div class="separator" style="clear: both; text-align: center;">[![](https://1.bp.blogspot.com/-hq4N5cTjojk/V6_aF10BTGI/AAAAAAAAD0M/wRFrhYttj9UVrlYhi1tGAARZkbaQO3XaACLcB/s1600/08.png)](https://1.bp.blogspot.com/-hq4N5cTjojk/V6_aF10BTGI/AAAAAAAAD0M/wRFrhYttj9UVrlYhi1tGAARZkbaQO3XaACLcB/s1600/08.png)</div>