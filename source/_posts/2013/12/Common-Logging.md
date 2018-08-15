---
title: Common.Logging
tags:
  - NLog
date: 2013-12-24 15:45:00
---

在開始使用log4net或NLog這種Logging元件來處理log，是一個很美好的開發經驗，但在開發類別庫專案的時後，會碰到循環參考的問題，這時後改用Common.Logging會比較好

Common.Logging是一個Log介面，可以支援log4net、NLog、Enterprise Library Logging，透過設定檔把Log轉接到真正要使用的Log元件，在日後轉換Log元件的時後很方便，詳細的介紹可以參考[官網](http://netcommon.sourceforge.net/)，以下用一個類別庫專案搭配一個應用程式來介紹這個元件的使用方式

Common.Logging 2.2.0版之後，相依於Common.Logging.Core套件
應該是為了可儶性，把介面和抽象類別分離到Core套件
在套件的使用上要做點調整

Common Logging 2.3.1版之後，已不再使用Common.Logging.Core
為了比較好在Log套件的多個版本之間切換，對應的Log套件後面都會有指定的版本
例如Common.Logging.NLog31對應到NLog 3.1版本

首先開啟一個類別庫專案，並透過NuGet加入Common.Logging參考
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-YZT52XVZA3Q/VHKbhm-Vn9I/AAAAAAAABvo/xwz2a-Mpg_Q/s1600/01.NuGet%E5%A5%97%E4%BB%B6.png)](http://1.bp.blogspot.com/-YZT52XVZA3Q/VHKbhm-Vn9I/AAAAAAAABvo/xwz2a-Mpg_Q/s1600/01.NuGet%E5%A5%97%E4%BB%B6.png)</div>

簡單寫一個函式讓之後引用的程式來呼叫
<div><pre class="brush:csharp">using Common.Logging;

namespace ClassLibrary1
{
    public class Class1
    {
        private ILog log = LogManager.GetLogger&lt;Class1&gt;());

        public void SayHello()
        {
            this.log.Info("Hello");
        }
    }
}
</pre></div>
再來新增一個Windows Form應用程式，並引用剛寫的庫別庫專案
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-xaXV4Oh0V4A/Urk59141GjI/AAAAAAAAA4o/tmXK3kNuKj0/s1600/02.ref.png)](http://4.bp.blogspot.com/-xaXV4Oh0V4A/Urk59141GjI/AAAAAAAAA4o/tmXK3kNuKj0/s1600/02.ref.png)</div>
簡單寫一個Button Click來呼叫類別庫中的函式
<div><pre class="brush:csharp">using System;
using System.Windows.Forms;

namespace WindowsFormsApplication1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            ClassLibrary1.Class1 x = new ClassLibrary1.Class1();
            x.SayHello();
        }
    }
}
</pre></div>
因為要轉接到NLog去，所以再新增套件Common.Logging.NLog31，對應的NLog版本就是3.1
如果要對應到其他的版本，可以選擇對應的套件
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-AE_fFBVrJSQ/VHKb3tGq9-I/AAAAAAAABvw/kRMfp3sX7nI/s1600/02.Nlog%E5%A5%97%E4%BB%B6.png)](http://3.bp.blogspot.com/-AE_fFBVrJSQ/VHKb3tGq9-I/AAAAAAAABvw/kRMfp3sX7nI/s1600/02.Nlog%E5%A5%97%E4%BB%B6.png)</div>
加入NLog，為了方便起見，順便加入NLog.Configuration和NLog Schema for Intellisense(TM)
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-Re1X-FNbZ0Q/VHKb71DU-_I/AAAAAAAABv4/rGS2CXpklXQ/s1600/03.Config%E5%A5%97%E4%BB%B6.png)](http://4.bp.blogspot.com/-Re1X-FNbZ0Q/VHKb71DU-_I/AAAAAAAABv4/rGS2CXpklXQ/s1600/03.Config%E5%A5%97%E4%BB%B6.png)</div>
接下來透過設定檔把Log轉接到NLog

<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;configuration&gt;
    &lt;configSections&gt;
        &lt;sectionGroup name="common"&gt;
            &lt;section name="logging" type="Common.Logging.ConfigurationSectionHandler, Common.Logging"/&gt;
        &lt;/sectionGroup&gt;
    &lt;/configSections&gt;
    &lt;common&gt;
        &lt;logging&gt;
            &lt;factoryAdapter type="Common.Logging.NLog.NLogLoggerFactoryAdapter, Common.Logging.NLog31"&gt;
                &lt;arg key="configType" value="FILE" /&gt;
                &lt;arg key="configFile" value="~/NLog.config" /&gt;
            &lt;/factoryAdapter&gt;
        &lt;/logging&gt;
    &lt;/common&gt;
    &lt;startup&gt;
        &lt;supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" /&gt;
    &lt;/startup&gt;
    &lt;runtime&gt;
        &lt;assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"&gt;
            &lt;dependentAssembly&gt;
                &lt;assemblyIdentity name="NLog" publicKeyToken="5120e14c03d0593c" culture="neutral" /&gt;
                &lt;bindingRedirect oldVersion="0.0.0.0-2.1.0.0" newVersion="2.1.0.0" /&gt;
            &lt;/dependentAssembly&gt;
        &lt;/assemblyBinding&gt;
    &lt;/runtime&gt;
&lt;/configuration&gt;
</pre></div>NLog使用預設的設定

<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;

    &lt;!-- 
  See http://nlog-project.org/wiki/Configuration_file 
  for information on customizing logging rules and outputs.
   --&gt;
    &lt;targets&gt;
        &lt;!-- add your targets here --&gt;
        &lt;target xsi:type="File" name="f" fileName="${basedir}/logs/${shortdate}.log"
                layout="${longdate} ${uppercase:${level}} ${message}" /&gt;

    &lt;/targets&gt;

    &lt;rules&gt;
        &lt;!-- add your logging rules here --&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="f" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div>輸出的結果
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-z3rA9UMH-kw/Urk7GkSlchI/AAAAAAAAA5E/NCuolISJCSY/s1600/05.result.png)](http://4.bp.blogspot.com/-z3rA9UMH-kw/Urk7GkSlchI/AAAAAAAAA5E/NCuolISJCSY/s1600/05.result.png)</div>