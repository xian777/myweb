---
title: 利用OctoPack套件打包Web專案
tags:
  - Octopus
date: 2014-09-29 16:18:00
---

首先開一個簡單的Web專案
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-At9zBC-g8H0/VCkVVV_qIlI/AAAAAAAABnc/FKQpNmjj5Pk/s1600/00.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://2.bp.blogspot.com/-At9zBC-g8H0/VCkVVV_qIlI/AAAAAAAABnc/FKQpNmjj5Pk/s1600/00.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>

透過NuGet安裝OctoPack套件
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-erYo_cgDq9M/VCkVaTdlNSI/AAAAAAAABnk/f9gARapVpLQ/s1600/01.%E5%AE%89%E8%A3%9DOctopack.png)](http://4.bp.blogspot.com/-erYo_cgDq9M/VCkVaTdlNSI/AAAAAAAABnk/f9gARapVpLQ/s1600/01.%E5%AE%89%E8%A3%9DOctopack.png)</div>

簡單寫一個批次檔來測試
<div><pre class="brush:shell">@echo off
set MSBUILD="C:\Program Files (x86)\MSBuild\12.0\bin\amd64\msbuild.exe"
if not exist %MSBUILD% (
 echo MSBuild not found
 exit
) 

%MSBUILD% WebApplication1.sln /p:Configuration=Release /p:RunOctoPack=true /m
pause
</pre></div>
編譯成功
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-JH4KBAfY3SI/VCkVj5U8T4I/AAAAAAAABns/xBUyl-VfTOI/s1600/02.%E7%B7%A8%E8%AD%AF%E6%88%90%E5%8A%9F.png)](http://3.bp.blogspot.com/-JH4KBAfY3SI/VCkVj5U8T4I/AAAAAAAABns/xBUyl-VfTOI/s1600/02.%E7%B7%A8%E8%AD%AF%E6%88%90%E5%8A%9F.png)</div>
bin資料夾下就會多了一個打包好的套件
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ST78E_TEKD4/VCkVnb3VHZI/AAAAAAAABn0/VkwlN2x6Ml8/s1600/03.%E6%89%93%E5%8C%85%E7%9A%84%E5%A5%97%E4%BB%B6.png)](http://2.bp.blogspot.com/-ST78E_TEKD4/VCkVnb3VHZI/AAAAAAAABn0/VkwlN2x6Ml8/s1600/03.%E6%89%93%E5%8C%85%E7%9A%84%E5%A5%97%E4%BB%B6.png)</div>