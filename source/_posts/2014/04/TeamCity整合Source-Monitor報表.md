---
title: TeamCity整合Source Monitor報表
tags:
  - Source Monitor
  - TeamCity
date: 2014-04-23 15:40:00
---

<div>Source Monitor是用來分析程式碼度量的工具，先到[官網](http://www.campwoodsw.com/sourcemonitor.html)下載</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-aUW-QXGVCtE/U1drxYfiw4I/AAAAAAAABSk/phO8_RBI2Os/s1600/01.%E4%B8%8B%E8%BC%89.png)](http://1.bp.blogspot.com/-aUW-QXGVCtE/U1drxYfiw4I/AAAAAAAABSk/phO8_RBI2Os/s1600/01.%E4%B8%8B%E8%BC%89.png)</div>
<div>安裝後的預設路徑為C:\Program Files (x86)\SourceMonitor</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-MKLglO_Layc/U1dr6iQoHSI/AAAAAAAABSs/JSEVH5l68VE/s1600/02.%E5%AE%89%E8%A3%9D%E8%B7%AF%E5%BE%91.png)](http://4.bp.blogspot.com/-MKLglO_Layc/U1dr6iQoHSI/AAAAAAAABSs/JSEVH5l68VE/s1600/02.%E5%AE%89%E8%A3%9D%E8%B7%AF%E5%BE%91.png)</div>
<div>先淮備一個用來產生報告的設定檔SourceMonitorCommands.xml</div>
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;sourcemonitor_commands&gt;
    &lt;write_log&gt;true&lt;/write_log&gt;
    &lt;command&gt;
        &lt;project_file&gt;SourceMonitor.smp&lt;/project_file&gt;
        &lt;checkpoint_name&gt;Baseline&lt;/checkpoint_name&gt;
        &lt;project_language&gt;C#&lt;/project_language&gt;
        &lt;!-- 要分析專案的相對路徑 --&gt;
        &lt;source_directory&gt;..&lt;/source_directory&gt;
        &lt;source_subdirectory_list&gt;
            &lt;exclude_subdirectories&gt;true&lt;/exclude_subdirectories&gt;
            &lt;source_subtree&gt;bin\&lt;/source_subtree&gt;
            &lt;source_subdirectory&gt;obj\&lt;/source_subdirectory&gt;
        &lt;/source_subdirectory_list&gt;
        &lt;parse_utf8_files&gt;True&lt;/parse_utf8_files&gt;
        &lt;ignore_headers_footers&gt;True&lt;/ignore_headers_footers&gt;
        &lt;export&gt;
            &lt;!-- 最後輸出的檔名 --&gt;
            &lt;export_file&gt;SourceMonitorReport.xml&lt;/export_file&gt;
            &lt;export_type&gt;2&lt;/export_type&gt;
        &lt;/export&gt;
    &lt;/command&gt;
&lt;/sourcemonitor_commands&gt;
</pre></div>
<div>因為輸出的是XML格式，所以需要透過XSL轉成HTML格式
先下載轉換的工具[msxsl.exe](http://www.microsoft.com/en-us/download/details.aspx?id=21714)</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-1zIhVE-ezj0/U1dsCkgZ1AI/AAAAAAAABS0/CSALVxR5RMw/s1600/03.%E4%B8%8B%E8%BC%89msxsl.png)](http://4.bp.blogspot.com/-1zIhVE-ezj0/U1dsCkgZ1AI/AAAAAAAABS0/CSALVxR5RMw/s1600/03.%E4%B8%8B%E8%BC%89msxsl.png)</div>
SourceMonitor.xsl</div><div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns="http://www.w3.org/TR/xhtml1/strict"&gt;
  &lt;xsl:output method="html"/&gt;

  &lt;xsl:template match="/"&gt;
  &lt;html&gt;
        &lt;head&gt;
        &lt;style type="text/css"&gt;
    /* 
 Web20 Table Style
 written by Netway Media, http://www.netway-media.com
*/
    table
    {
        border-collapse: collapse;
        border: 1px solid #666666;
        font: normal 11px verdana, arial, helvetica, sans-serif;
        color: #363636;
        background: #f6f6f6;
        text-align: left;
    }
    caption
    {
        text-align: center;
        font: bold 16px arial, helvetica, sans-serif;
        background: transparent;
        padding: 6px 4px 8px 0px;
        color: #CC00FF;
        text-transform: uppercase;
    }
    thead, tfoot
    {
        background: url(bg1.png) repeat-x;
        text-align: left;
        height: 30px;
    }
    thead th, tfoot th
    {
        padding: 5px;
    }
    table a
    {
        color: #333333;
        text-decoration: none;
    }
    table a:hover
    {
        text-decoration: underline;
    }
    tr.odd
    {
        background: #f1f1f1;
    }
    tbody th, tbody td
    {
        padding: 5px;
        padding-left: 10px;
    }
    td.sectionheader
    {
        color: Navy;
        font-size: 20px;
        font-weigth: bold;
        text-align: center;
    }
&lt;/style&gt;
        &lt;/head&gt;
        &lt;body&gt;
    &lt;xsl:apply-templates select="//SourceMonitorComplexitySummary" /&gt;     
    &lt;/body&gt;
    &lt;/html&gt;
  &lt;/xsl:template&gt;

 &lt;!-- The most complex methods --&gt;
  &lt;xsl:template match="SourceMonitorComplexitySummary"&gt;
    &lt;table class="section-table" cellpadding="2" cellspacing="0" border="0" width="98%"&gt;
      &lt;!--&lt;colgroup&gt;
        &lt;col width="300px" /&gt;
        &lt;col width="50px" /&gt;
        &lt;col /&gt;
        &lt;col width="50px" /&gt;
      &lt;/colgroup&gt;--&gt;
      &lt;tr&gt;
        &lt;td class="sectionheader" colspan="4"&gt;
           SourceMonitor - &lt;xsl:value-of select="count(MostComplexMethods/Method)" /&gt; Most Complex Methods
        &lt;/td&gt;
      &lt;/tr&gt;
      &lt;tr&gt;
        &lt;th class="header-label"&gt;
          Complexity
        &lt;/th&gt;
        &lt;th class="header-label"&gt;
          File
        &lt;/th&gt;
        &lt;th class="header-label"&gt;
          Method
        &lt;/th&gt;        
        &lt;th class="header-label"&gt;
          Line
        &lt;/th&gt;
      &lt;/tr&gt;
      &lt;xsl:apply-templates select="MostComplexMethods/Method" /&gt;
    &lt;/table&gt;

    &lt;br/&gt;

    &lt;!-- The most deeply nested code blocks --&gt;
    &lt;table class="section-table" cellpadding="2" cellspacing="0" border="0" width="98%"&gt;
      &lt;!--&lt;colgroup&gt;
        &lt;col width="50px"/&gt;
        &lt;col /&gt;
        &lt;col width="50px" /&gt;
      &lt;/colgroup&gt;--&gt;
      &lt;tr&gt;
        &lt;td class="sectionheader" colspan="4"&gt;           
           SourceMonitor - &lt;xsl:value-of select="count(MostDeeplyNestedCode/Block)" /&gt; Most Deeply Nested Code Blocks
        &lt;/td&gt;
      &lt;/tr&gt;
      &lt;tr&gt;
        &lt;th class="header-label"&gt;
          Depth
        &lt;/th&gt;
        &lt;th class="header-label"&gt;
          File
        &lt;/th&gt;
        &lt;th class="header-label"&gt;
          Line
        &lt;/th&gt;
      &lt;/tr&gt;
      &lt;xsl:apply-templates select="MostDeeplyNestedCode/Block" /&gt;
    &lt;/table&gt;
  &lt;/xsl:template&gt;

  &lt;!-- Complex Method List --&gt;
  &lt;xsl:template match="MostComplexMethods/Method"&gt;
      &lt;tr&gt;
        &lt;xsl:if test="position() mod 2 = 1"&gt;
          &lt;xsl:attribute name="class"&gt;section-oddrow odd&lt;/xsl:attribute&gt;          
        &lt;/xsl:if&gt;
        &lt;td&gt;
          &lt;xsl:value-of select="Complexity" /&gt;
        &lt;/td&gt;
        &lt;td &gt;
          &lt;xsl:value-of select="File" /&gt;
        &lt;/td&gt;
        &lt;td&gt;
          &lt;xsl:value-of select="Name"/&gt;
        &lt;/td&gt;        
        &lt;td&gt;
          &lt;xsl:value-of select="Line" /&gt;
        &lt;/td&gt;
      &lt;/tr&gt;
  &lt;/xsl:template&gt;

  &lt;!-- Deeply Nested Blocks List --&gt;
  &lt;xsl:template match="MostDeeplyNestedCode/Block"&gt;
      &lt;tr&gt;
        &lt;xsl:if test="position() mod 2 = 1"&gt;
          &lt;xsl:attribute name="class"&gt;section-oddrow odd&lt;/xsl:attribute&gt;
        &lt;/xsl:if&gt;
        &lt;td&gt;
          &lt;xsl:value-of select="Depth" /&gt;
        &lt;/td&gt;
        &lt;td&gt;
          &lt;xsl:value-of select="File" /&gt;
        &lt;/td&gt;
        &lt;td&gt;
          &lt;xsl:value-of select="Line" /&gt;
        &lt;/td&gt;
      &lt;/tr&gt;
  &lt;/xsl:template&gt;

&lt;/xsl:stylesheet&gt;
<span style="font-family: Times New Roman;"><span style="white-space: normal;">
</span></span></pre></div>
SourceMonitorSummaryGeneration.xsl
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="UTF-8" ?&gt;
&lt;xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"&gt;

  &lt;!--- SourceMonitor Summary Xml File Generation created by Eden Ridgway --&gt;
  &lt;xsl:output method="xml"/&gt;

  &lt;xsl:template match="/"&gt;
    &lt;xsl:apply-templates select="/sourcemonitor_metrics" /&gt;
  &lt;/xsl:template&gt;

  &lt;!-- Transform the results into a simpler more intuitive and summarised format --&gt;
  &lt;xsl:template match="sourcemonitor_metrics"&gt;
      &lt;SourceMonitorComplexitySummary&gt;
        &lt;MostComplexMethods&gt;
          &lt;xsl:call-template name="MostComplexMethods"/&gt;
        &lt;/MostComplexMethods&gt;

        &lt;LinePerMethod&gt;
          &lt;xsl:call-template name="LinesPerMethod"/&gt;
        &lt;/LinePerMethod&gt;

        &lt;MostDeeplyNestedCode&gt;
          &lt;xsl:call-template name="MostDeeplyNestedCode"/&gt;
        &lt;/MostDeeplyNestedCode&gt;

      &lt;/SourceMonitorComplexitySummary&gt;
  &lt;/xsl:template&gt;

  &lt;!-- Complexity Metrics --&gt;
  &lt;xsl:template name="MostComplexMethods"&gt;
    &lt;xsl:for-each select=".//file"&gt;
      &lt;xsl:sort select="metrics/metric[@id='M10']" order="descending" data-type="number" /&gt;

      &lt;xsl:choose&gt;
        &lt;xsl:when test="position() &amp;lt; 16"&gt;
           &lt;Method&gt;
              &lt;File&gt;&lt;xsl:value-of select="@file_name"/&gt;&lt;/File&gt;
              &lt;Name&gt;&lt;xsl:value-of select="metrics/metric[@id='M9']"/&gt;&lt;/Name&gt;
              &lt;Line&gt;&lt;xsl:value-of select="metrics/metric[@id='M8']"/&gt;&lt;/Line&gt;
              &lt;Complexity&gt;&lt;xsl:value-of select="metrics/metric[@id='M10']"/&gt;&lt;/Complexity&gt;
           &lt;/Method&gt;
        &lt;/xsl:when&gt;
      &lt;/xsl:choose&gt;
    &lt;/xsl:for-each&gt;
  &lt;/xsl:template&gt;

  &lt;!-- Complexity Metrics --&gt;
  &lt;xsl:template name="LinesPerMethod"&gt;
    &lt;xsl:for-each select=".//file"&gt;
      &lt;xsl:sort select="metrics/metric[@id='M5']" order="descending" data-type="number" /&gt;

      &lt;xsl:choose&gt;
        &lt;xsl:when test="position() &amp;lt; 16"&gt;
           &lt;Method&gt;
              &lt;File&gt;&lt;xsl:value-of select="@file_name"/&gt;&lt;/File&gt;
              &lt;Lines&gt;&lt;xsl:value-of select="metrics/metric[@id='M5']"/&gt;&lt;/Lines&gt;
           &lt;/Method&gt;
        &lt;/xsl:when&gt;
      &lt;/xsl:choose&gt;
    &lt;/xsl:for-each&gt;
  &lt;/xsl:template&gt;

  &lt;!-- Nesting Metrics --&gt;
  &lt;xsl:template name="MostDeeplyNestedCode"&gt;
    &lt;xsl:for-each select=".//file"&gt;
        &lt;xsl:sort select="metrics/metric[@id='M12']" order="descending" data-type="text" /&gt;

        &lt;xsl:choose&gt;
          &lt;xsl:when test="position() &amp;lt; 16"&gt;
             &lt;Block&gt;
                &lt;File&gt;&lt;xsl:value-of select="@file_name"/&gt;&lt;/File&gt;
                &lt;Depth&gt;&lt;xsl:value-of select="metrics/metric[@id='M12']"/&gt;&lt;/Depth&gt;
                &lt;Line&gt;&lt;xsl:value-of select="metrics/metric[@id='M11']"/&gt;&lt;/Line&gt;
             &lt;/Block&gt;
          &lt;/xsl:when&gt;
        &lt;/xsl:choose&gt;
    &lt;/xsl:for-each&gt;
  &lt;/xsl:template&gt;

&lt;/xsl:stylesheet&gt;

</pre></div>
<div>透過批次檔得到HTML格式</div><div><pre class="brush:bash">SourceMonitor.exe /C SourceMonitorCommands.xml
msxsl.exe SourceMonitorReport.xml SourceMonitorSummaryGeneration.xsl -o SourceMonitorSummaryGeneration.xml
msxsl.exe SourceMonitorSummaryGeneration.xml SourceMonitor.xsl -o SourceMonitorResult.html
</pre></div>
<div>在TeamCity上面利用Command Line的Build Step來產出檔案
方便請見所以建立一個SourceMonitor的資料夾，把相關的執行檔和設定檔都放進去</div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-fB6efdi3sLY/U1dt1d9N2lI/AAAAAAAABTo/sM9uAiTT144/s1600/04.%E5%BB%BA%E7%BD%AE%E5%8B%95%E4%BD%9C.png)](http://2.bp.blogspot.com/-fB6efdi3sLY/U1dt1d9N2lI/AAAAAAAABTo/sM9uAiTT144/s1600/04.%E5%BB%BA%E7%BD%AE%E5%8B%95%E4%BD%9C.png)</div>
<div>新增一個建置報告</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-d6YFhZeqscQ/U1dsmWfvj9I/AAAAAAAABTE/m8iJnDT3NjY/s1600/05.%E6%96%B0%E5%A2%9EBuild+Report.png)](http://3.bp.blogspot.com/-d6YFhZeqscQ/U1dsmWfvj9I/AAAAAAAABTE/m8iJnDT3NjY/s1600/05.%E6%96%B0%E5%A2%9EBuild+Report.png)</div>給一個用來識別的名稱和輸入產生的檔案
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-HWTCgjCV7ao/U1dsw1-UY8I/AAAAAAAABTM/agiFf-B1Uqk/s1600/06.Build+Report.png)](http://1.bp.blogspot.com/-HWTCgjCV7ao/U1dsw1-UY8I/AAAAAAAABTM/agiFf-B1Uqk/s1600/06.Build+Report.png)</div>
在一般設定中的Artifact Paths加入輸出的檔案
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-M548qVSUE3s/U1dtAFUY41I/AAAAAAAABTU/mgfaj3i2UV8/s1600/07.%E4%B8%80%E8%88%AC%E8%A8%AD%E5%AE%9A.png)](http://4.bp.blogspot.com/-M548qVSUE3s/U1dtAFUY41I/AAAAAAAABTU/mgfaj3i2UV8/s1600/07.%E4%B8%80%E8%88%AC%E8%A8%AD%E5%AE%9A.png)</div>

<div>設定正確的話，建置後就可以看到這個報表了</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-aMSRvswmn08/U1dtFFT5nKI/AAAAAAAABTc/ClKODzPaZFo/s1600/08.Report.png)](http://4.bp.blogspot.com/-aMSRvswmn08/U1dtFFT5nKI/AAAAAAAABTc/ClKODzPaZFo/s1600/08.Report.png)</div>

<div>參考資料
[CI Server 16 - 整合程式碼複雜度及深度報表 (Source Monitor)](http://ithelp.ithome.com.tw/question/10107051)</div>