---
title: app.config Transformations
tags:
  - app.config
  - XDT Transform
date: 2012-08-18 17:58:00
---

<div class="separator" style="clear: both; text-align: left;">使用過內建的web.config transform功能，對於佈署不同環境時更新設定檔內容很有幫助</div><div class="separator" style="clear: both; text-align: left;">但app.config並沒有這樣的功能，之前搜尋了一些解法，大部份是自行修改專案檔，並利用MSBuild來轉換XML檔案</div><div class="separator" style="clear: both; text-align: left;">那一次研究到頭暈眼花還搞不定，就暫時放下，改天境界有所提升再來研究</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">最近又想到這個問題，趁著失眠的時後再來摸一下，應該可以很快就睡著XD</div><div class="separator" style="clear: both; text-align: left;">結果找到了這個套件，用滑鼠點一點就搞定了，使用上方便多了</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">首先先下載SlowCheetah這個套件</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">![](http://2.bp.blogspot.com/-qYHWl1ly1h8/UC9h5CNSEvI/AAAAAAAAAAk/LCxj2KxwLYk/s640/01.SlowCheetah.png)</div><div style="text-align: left;">
</div><div style="text-align: left;">安裝並重新啟動後，在app.config上面點右鍵，會出現這個Add Transform功能選項 </div><div class="separator" style="clear: both; text-align: left;">[![](http://3.bp.blogspot.com/-eD-oI9lRbjQ/UC9h51R2VZI/AAAAAAAAAAo/RL1zOHSjxrU/s640/02.AddTransform.png)](http://3.bp.blogspot.com/-eD-oI9lRbjQ/UC9h51R2VZI/AAAAAAAAAAo/RL1zOHSjxrU/s1600/02.AddTransform.png)</div><div style="text-align: left;">
</div><div style="text-align: left;">按下後，會跳出一個警告視窗，提示會修改你的專案檔來完成app.config的轉換功能</div><div class="separator" style="clear: both; text-align: left;">[![](http://3.bp.blogspot.com/-hZFwvWz7Jn4/UC9h6tFmWtI/AAAAAAAAAAs/ZmaHtC_mDzo/s640/03.Alert.png)](http://3.bp.blogspot.com/-hZFwvWz7Jn4/UC9h6tFmWtI/AAAAAAAAAAs/ZmaHtC_mDzo/s1600/03.Alert.png)</div><div style="text-align: left;">
</div><div style="text-align: left;">按下「是」後 ，會自動幫你依組態新增出對應的config檔案</div><div class="separator" style="clear: both; text-align: left;">[![](http://3.bp.blogspot.com/-dyVGcKN93PQ/UC9lbptDKlI/AAAAAAAAABc/heOoWKUG5Cs/s400/035+Result.png)](http://3.bp.blogspot.com/-dyVGcKN93PQ/UC9lbptDKlI/AAAAAAAAABc/heOoWKUG5Cs/s1600/035+Result.png)</div><div style="text-align: left;">這是一個簡單的設定檔內容  
<pre class="brush: xml"> 
&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;configuration&gt;

 &lt;appSettings&gt;
  &lt;add key="ServerIP" value="127.0.0.1" /&gt;
 &lt;/appSettings&gt;

 &lt;connectionStrings&gt;
  &lt;add name="MyDB" providerName="System.Data.SqlClient"
    connectionString="Data Source=(local);Initial Catalog=DemoDB;Integrated Security=True"/&gt;
 &lt;/connectionStrings&gt;

&lt;/configuration&gt;
</pre></div><div class="separator" style="clear: both; text-align: left;">[
](http://4.bp.blogspot.com/-d5ooCTpJduw/UC9h7UK21rI/AAAAAAAAAA0/KoVsJKcykvU/s1600/04.App.Config.png)</div><div style="text-align: left;">在Debug組態的設定檔中，改變了設定檔的內容 
<pre class="brush: xml"> 
&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;!-- For more information on using transformations 
     see the web.config examples at http://go.microsoft.com/fwlink/?LinkId=214134\. --&gt;
&lt;configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform"&gt;
 &lt;appSettings&gt;
  &lt;add key="ServerIP" value="192.168.100.11" 
    xdt:Transform="SetAttribute" xdt:Locator="Match(key)" /&gt;
 &lt;/appSettings&gt;

 &lt;connectionStrings&gt;
  &lt;add name="MyDB" connectionString="Data Source=192.168.100.11;Initial Catalog=DemoDB;uid=ooo;pwd=xxx;"
    xdt:Transform="SetAttribute" xdt:Locator="Match(key)" /&gt;
 &lt;/connectionStrings&gt;
&lt;/configuration&gt;&nbsp;</pre><pre class="brush: xml">&nbsp;</pre></div><div class="separator" style="clear: both; text-align: left;"></div><div style="text-align: left;">在Release組態中也是改變了設定檔的內容 
<pre class="brush: xml"> 
&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;!-- For more information on using transformations 
     see the web.config examples at http://go.microsoft.com/fwlink/?LinkId=214134\. --&gt;
&lt;configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform"&gt;
 &lt;appSettings&gt;
  &lt;add key="ServerIP" value="10.8.200.11"
    xdt:Transform="SetAttribute" xdt:Locator="Match(key)" /&gt;
 &lt;/appSettings&gt;

 &lt;connectionStrings&gt;
  &lt;add name="MyDB" connectionString="Data Source=10.8.200.11;Initial Catalog=DemoDB;uid=###;pwd=***;"
    xdt:Transform="SetAttribute" xdt:Locator="Match(key)" /&gt;
 &lt;/connectionStrings&gt;
&lt;/configuration&gt;
</pre></div><div class="separator" style="clear: both; text-align: left;"></div><div class="separator" style="clear: both; text-align: left;"></div><div class="separator" style="clear: both; text-align: left;"></div><div class="separator" style="clear: both; text-align: left;"></div><div style="text-align: left;">
</div><div style="text-align: left;"></div><div style="text-align: left;">
</div><div style="text-align: left;">參考連結：</div><div style="text-align: left;">
</div><div style="text-align: left;">[App.Config Transformation for projects which are not Web Projects in Visual Studio 2010? ](http://stackoverflow.com/questions/3004210/app-config-transformation-for-projects-which-are-not-web-projects-in-visual-stud)</div><div style="text-align: left;"></div><div style="text-align: left;">
</div><div style="text-align: left;">[SlowCheetah - XML Transforms ](http://visualstudiogallery.msdn.microsoft.com/69023d00-a4f9-4a34-a6cd-7e854ba318b5)</div><div style="text-align: left;">
</div><div style="text-align: left;"></div><div style="text-align: left;">[使用 Visual Studio 之 Web 應用程式專案部署的 Web.config 轉換語法 ](http://msdn.microsoft.com/zh-tw/library/dd465326.aspx)</div>