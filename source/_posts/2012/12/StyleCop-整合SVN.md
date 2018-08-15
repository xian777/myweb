---
title: StyleCop 整合SVN
tags:
  - StyleCop
date: 2012-12-24 20:18:00
---

## 安裝SVNStyleCop
1\. 首先[下載SVNStyleCop安裝檔](http://svnstylecop.codeplex.com/)
2\. 解壓縮後編輯SVNStyleCop.exe.config
3\. 設定SVNSettings.StyleCop裡面要檢查的規則
4\. 修改SVNStyleCop.exe.config裡面的路徑範本
<pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;configuration&gt;
    &lt;configSections&gt;
        &lt;section name="svnStyleCopConfig" type="SVNStyleCop.SvnStyleCopConfigSection, SVNStyleCop" allowDefinition="Everywhere" allowExeDefinition="MachineToApplication" restartOnExternalChanges="true" /&gt;
    &lt;/configSections&gt;

    &lt;svnStyleCopConfig tempFolder="Temp"&gt;
        &lt;!-- 設定svnlook.exe執行檔位置 --&gt;
        &lt;svnLook location="C:\Program Files\VisualSVN Server\bin\svnlook.exe" /&gt;
        &lt;styleCop settingsFile="SVNSettings.StyleCop" maxViolationCount="20" /&gt;

        &lt;!-- 設定專案路徑範本 --&gt;
        &lt;pathPatterns&gt;
            &lt;clear /&gt;
            &lt;add value="^trunk/.*\.cs$"/&gt;
   &lt;add value="^branches/.*\.cs$"/&gt;
   &lt;add value="^tags/.*\.cs$"/&gt;
        &lt;/pathPatterns&gt;
    &lt;/svnStyleCopConfig&gt;

&lt;/configuration&gt;</pre>

## 設定
<div>1\. 編輯壓縮檔下面的pre-commit.cmd，修改前兩行svnlook.exe和SVNStyleCop.exe的路徑</div><div>2\. 把批次檔的內容複製到SVN Repos的pre-commit hook</div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-87zwTSTxMa0/UOPNcTue3SI/AAAAAAAAApY/zcxgaQcFXAs/s1600/01.Hook.png)](http://3.bp.blogspot.com/-87zwTSTxMa0/UOPNcTue3SI/AAAAAAAAApY/zcxgaQcFXAs/s1600/01.Hook.png)</div><div>
</div>
<div class="separator" style="clear: both; text-align: left;"></div>

### 參考資料
[SVNStyleCop官網](http://svnstylecop.codeplex.com/)