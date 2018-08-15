---
title: Windows Service 啟動參數
tags:
  - 'C#'
  - windows service
date: 2014-01-20 18:13:00
---

Windows Service可以透過幾種方式來傳入啟動參數
可以利用服務的啟動參數
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-23WhzTbJ75Y/UtzyuOGrojI/AAAAAAAAA-Q/Pnyc88yUKcw/s1600/02.%E5%95%9F%E5%8B%95%E5%8F%83%E6%95%B8.png)](http://1.bp.blogspot.com/-23WhzTbJ75Y/UtzyuOGrojI/AAAAAAAAA-Q/Pnyc88yUKcw/s1600/02.%E5%95%9F%E5%8B%95%E5%8F%83%E6%95%B8.png)</div>
OnStart就可以收到參數
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-0B5CCS1rGhc/UtzyyZKFSGI/AAAAAAAAA-Y/sCbNvZRXSdg/s1600/03.Args.png)](http://2.bp.blogspot.com/-0B5CCS1rGhc/UtzyyZKFSGI/AAAAAAAAA-Y/sCbNvZRXSdg/s1600/03.Args.png)</div>
<span style="color: red;">但需要注意這種方式只能設定一次，下次啟動還要再設定才行</span>
透過命令列的話有兩種方式
net start service1 /3000 /yyyyMMddHHmmss
但這種方式收到的參數也會有斜線
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-lwImaTWKjac/Utz0jVWsL2I/AAAAAAAAA-k/j-Sc7uTxWoc/s1600/07.%E6%9C%89%E6%96%9C%E7%B7%9A.png)](http://2.bp.blogspot.com/-lwImaTWKjac/Utz0jVWsL2I/AAAAAAAAA-k/j-Sc7uTxWoc/s1600/07.%E6%9C%89%E6%96%9C%E7%B7%9A.png)</div>
sc start service1 3000 yyyyMMddHHmmss
這種方式就不會有斜線了

還有一種方式是設定在服務機碼的ImagePath後面
需要透過覆寫安裝程式的Install函式來完成
<div><pre class="brush:csharp">using System.Collections;
using System.ComponentModel;
using Microsoft.Win32;

namespace MyService
{
    [RunInstaller(true)]
    public partial class ProjectInstaller : System.Configuration.Install.Installer
    {
        public ProjectInstaller()
        {
            InitializeComponent();
        }

        public override void Install(IDictionary stateSaver)
        {
            base.Install(stateSaver);

            // 安裝的時後增加啟動參數
            RegistryKey System = Registry.LocalMachine.OpenSubKey("System");
            RegistryKey currentControlSet = System.OpenSubKey("CurrentControlSet");
            RegistryKey services = currentControlSet.OpenSubKey("Services");
            RegistryKey service = services.OpenSubKey(this.serviceInstaller1.ServiceName, true);
            string imagePath = service.GetValue("ImagePath") + " 3000 yyyyMMddHHmmss";
            service.SetValue("ImagePath", imagePath);
            service.Close();
        }
    }
}

</pre></div>
服務的內容就會在執行路徑後面帶上參數
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-UUq9LvzYQ9s/Utz0-hjTDAI/AAAAAAAAA-0/Z_xDcHxKKoY/s1600/04.ImagePath.png)](http://4.bp.blogspot.com/-UUq9LvzYQ9s/Utz0-hjTDAI/AAAAAAAAA-0/Z_xDcHxKKoY/s1600/04.ImagePath.png)</div>透過Environment.GetCommandLineArgs()來取得參數
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-x4WCgs2qNMo/Utz2Ak-MkHI/AAAAAAAAA_I/0KkslrpmTMQ/s1600/05.GetCommandLineArgs.png)](http://1.bp.blogspot.com/-x4WCgs2qNMo/Utz2Ak-MkHI/AAAAAAAAA_I/0KkslrpmTMQ/s1600/05.GetCommandLineArgs.png)</div>
<span style="color: red;">只不過這種參數方式是需要修改機碼，所以設定上不太方便</span>

最簡單好用的方式，莫過於透過app.config中的appSettings
<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;configuration&gt;
    &lt;configSections&gt;
        &lt;sectionGroup name="common"&gt;
            &lt;section name="logging" type="Common.Logging.ConfigurationSectionHandler, Common.Logging"/&gt;
        &lt;/sectionGroup&gt;
    &lt;/configSections&gt;
    &lt;common&gt;
        &lt;logging&gt;
            &lt;factoryAdapter type="Common.Logging.NLog.NLogLoggerFactoryAdapter, Common.Logging.NLog"&gt;
                &lt;arg key="configType" value="FILE" /&gt;
                &lt;arg key="configFile" value="~/NLog.config" /&gt;
            &lt;/factoryAdapter&gt;
        &lt;/logging&gt;
    &lt;/common&gt;
    &lt;appSettings&gt;
        &lt;add key="TimerInterval" value="3000" /&gt;
        &lt;add key="DateTimeFormat" value="HH:mm:ss yyyy/MM/dd" /&gt;
    &lt;/appSettings&gt;
    &lt;startup&gt;
        &lt;supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" /&gt;
    &lt;/startup&gt;
    &lt;runtime&gt;
        &lt;assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"&gt;
            &lt;dependentAssembly&gt;
                &lt;assemblyIdentity name="NLog" publicKeyToken="5120e14c03d0593c" culture="neutral" /&gt;
                &lt;bindingRedirect oldVersion="0.0.0.0-2.1.0.0" newVersion="2.1.0.0" /&gt;
            &lt;/dependentAssembly&gt;
            &lt;dependentAssembly&gt;
                &lt;assemblyIdentity name="Common.Logging" publicKeyToken="af08829b84f0328e" culture="neutral" /&gt;
                &lt;bindingRedirect oldVersion="0.0.0.0-2.1.2.0" newVersion="2.1.2.0" /&gt;
            &lt;/dependentAssembly&gt;
        &lt;/assemblyBinding&gt;
    &lt;/runtime&gt;
&lt;/configuration&gt;
</pre></div>
記得要引用System.Configuration參考
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-MCi8mOBjr8o/Utz1SMcvjLI/AAAAAAAAA-8/ytnE2aN3h6s/s1600/06.System.Configuration.png)](http://4.bp.blogspot.com/-MCi8mOBjr8o/Utz1SMcvjLI/AAAAAAAAA-8/ytnE2aN3h6s/s1600/06.System.Configuration.png)</div>
啟動的時後取出參數傳入就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-SobbyJex93Y/Utz2kaEy_5I/AAAAAAAAA_Q/3mmshi85rrs/s1600/08.%E8%A8%AD%E5%AE%9A%E6%AA%94.png)](http://1.bp.blogspot.com/-SobbyJex93Y/Utz2kaEy_5I/AAAAAAAAA_Q/3mmshi85rrs/s1600/08.%E8%A8%AD%E5%AE%9A%E6%AA%94.png)</div>