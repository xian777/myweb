---
title: Windows Service 開發
tags:
  - 'C#'
  - windows service
date: 2014-01-20 13:45:00
---

Windows Service是一種沒有UI，開機後不需使用者登入就會執行的應用程式，通常會用來做一些定時排程的工作。
用C#開發Windows Service很簡單，以下用一個簡單的範例來介紹
<div>
</div><div>首先開一個新專案，名稱為MyService</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-nPZ1TWcF_gE/UtyZHPYoD6I/AAAAAAAAA5U/PmOegTcO0ZQ/s1600/01.NewProject.png)](http://4.bp.blogspot.com/-nPZ1TWcF_gE/UtyZHPYoD6I/AAAAAAAAA5U/PmOegTcO0ZQ/s1600/01.NewProject.png)</div>
</div><div>在方案總管中可以看到，只有Program.cs和Service1.cs兩個檔案</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-67GklNvhUr4/UtyZTsHucXI/AAAAAAAAA5c/tGlNpdjspvM/s1600/02.%E6%96%B9%E6%A1%88%E7%B8%BD%E7%AE%A1.png)](http://3.bp.blogspot.com/-67GklNvhUr4/UtyZTsHucXI/AAAAAAAAA5c/tGlNpdjspvM/s1600/02.%E6%96%B9%E6%A1%88%E7%B8%BD%E7%AE%A1.png)</div>
</div><div>先來看看Program.cs，這是應用程式的進入點，主要是透過ServiceBase.Run來啟動服務</div><div><pre class="brush:csharp">using System.ServiceProcess;

namespace MyService
{
    static class Program
    {
        /// &lt;summary&gt;
        /// 應用程式的主要進入點。
        /// &lt;/summary&gt;
        static void Main()
        {
            ServiceBase[] ServicesToRun;
            ServicesToRun = new ServiceBase[] 
            { 
                new Service1() 
            };
            ServiceBase.Run(ServicesToRun);
        }
    }
}

</pre></div><div>再來看一下Service1.cs，可以看到是繼承自ServiceBase的類別，再自行覆寫要處理的事件</div><div><pre class="brush:csharp">using System.ServiceProcess;

namespace MyService
{
    public partial class Service1 : ServiceBase
    {
        public Service1()
        {
            InitializeComponent();
        }

        protected override void OnStart(string[] args)
        {
        }

        protected override void OnStop()
        {
        }
    }
}

</pre></div><div>可覆寫的方法如下</div><div><table><tbody><tr><td>OnContinue</td><td>指定暫停服務後要繼續正常運作所要執行的動作</td></tr><tr><td>OnCustomCommand</td><td>指定在具有指定參數值的命令發生時所要執行的動作
<span style="color: red;">需要注意命令編號為128~256</span></td></tr><tr><td>OnPause</td><td>指定在服務暫停時所要執行的動作</td></tr><tr><td>OnPowerEvent</td><td>這適用於攜帶型電腦，當它們進入暫停模式的時候，不同於系統關閉</td></tr><tr><td>OnSessionChange</td><td>當從 Terminal Server 工作階段接收到變更事件時執行</td></tr><tr><td>OnShutdown</td><td>指定緊接在系統關閉之前應該發生的處理</td></tr><tr><td>OnStart</td><td>指定在服務啟動時所要執行的動作</td></tr><tr><td>OnStop</td><td>指定在服務停止執行時所要執行的動作</td></tr></tbody></table></div><div>
可設定的屬性如下，最常用的還是ServiceName這個屬性</div><div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-mAXtu_uATeY/UtybEa1AujI/AAAAAAAAA5w/INeITSD60RY/s1600/03.ServiceBase%E5%B1%AC%E6%80%A7.png)](http://3.bp.blogspot.com/-mAXtu_uATeY/UtybEa1AujI/AAAAAAAAA5w/INeITSD60RY/s1600/03.ServiceBase%E5%B1%AC%E6%80%A7.png)</div>
</div><div>更詳細的內容可以參考MSDN關於[ServiceBase](http://msdn.microsoft.com/zh-tw/library/system.serviceprocess.servicebase(v=vs.110).aspx)的介紹</div><div>
</div><div>先來簡單地寫個定時功能
透過Log元件輸出目前時間到Log2Console
相關內容可以參考之前的筆記
[Common.Logging](http://blog.developer.idv.tw/2013/12/commonlogging.html)
[好用的LogViewer](http://blog.developer.idv.tw/2013/11/logviewer.html)

</div><div><pre class="brush:csharp">using System;
using System.ServiceProcess;
using System.Timers;
using Common.Logging;

namespace MyService
{
    public partial class Service1 : ServiceBase
    {
        private Timer timer;
        private ILog log;
        private string datetimeFormat = "yyyy/MM/dd HH:mm:ss";
        private double timerInterval = 1000;

        public Service1()
        {
            InitializeComponent();
            this.log = LogManager.GetLogger(typeof(Service1));
            this.timer = new Timer();
            this.timer.Interval = this.timerInterval;
            this.timer.AutoReset = false;
            this.timer.Enabled = false;
            this.timer.Elapsed += Timer_Elapsed;
        }

        protected override void OnStart(string[] args)
        {
            this.timer.Enabled = true;
        }

        protected override void OnStop()
        {
            this.timer.Enabled = false;
        }

        private void Timer_Elapsed(object sender, ElapsedEventArgs e)
        {
            this.timer.Stop();

            try
            {
                this.log.TraceFormat("now:{0}", DateTime.Now.ToString(this.datetimeFormat));
            }
            catch (Exception ex)
            {
                this.log.Error(ex);
            }

            this.timer.Start();
        }
    }
}

</pre></div><div>接下來要增加安裝程式，在Service1.cs的設計畫面按右鍵，選擇加入安裝程式</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-ovn0HIpEK38/UtybIw9JreI/AAAAAAAAA54/_d1_EmcvqEE/s1600/04.%E5%8A%A0%E5%85%A5%E5%AE%89%E8%A3%9D%E7%A8%8B%E5%BC%8F.png)](http://4.bp.blogspot.com/-ovn0HIpEK38/UtybIw9JreI/AAAAAAAAA54/_d1_EmcvqEE/s1600/04.%E5%8A%A0%E5%85%A5%E5%AE%89%E8%A3%9D%E7%A8%8B%E5%BC%8F.png)</div>
</div><div>會增加一個繼承自System.Configuration.Install.Installer的ProjectInstaller類別</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-UKW0EPYGkkk/UtybMznln5I/AAAAAAAAA6A/aoHnh0w5gwU/s1600/05.Projectnstaller.png)](http://3.bp.blogspot.com/-UKW0EPYGkkk/UtybMznln5I/AAAAAAAAA6A/aoHnh0w5gwU/s1600/05.Projectnstaller.png)</div>
</div><div>先設定服務執行時使用的帳號，比較安全的帳號是NetworkService，如果有需要存取資源的話，再去允許權限或是改用LocalSystem這個帳號</div><div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-CYoBSMIfZj4/Utybkt47AiI/AAAAAAAAA6Q/9Y5H4xUtBd4/s1600/06.%E7%99%BB%E5%85%A5%E5%B8%B3%E8%99%9F.png)](http://1.bp.blogspot.com/-CYoBSMIfZj4/Utybkt47AiI/AAAAAAAAA6Q/9Y5H4xUtBd4/s1600/06.%E7%99%BB%E5%85%A5%E5%B8%B3%E8%99%9F.png)</div>
</div><div>接下來設定服務的啟動方式，最常用的當然是自動啟動
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-iS03_xS0ewU/UtyfYhnVFPI/AAAAAAAAA68/CN4arzq-Q3Y/s1600/07.AotuMatic.png)](http://2.bp.blogspot.com/-iS03_xS0ewU/UtyfYhnVFPI/AAAAAAAAA68/CN4arzq-Q3Y/s1600/07.AotuMatic.png)</div>
</div><div>DisplayName是名稱，Description描述</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-sK3GlrDv3cQ/Utybu00xq_I/AAAAAAAAA6g/_omh1Cvm4xA/s1600/08.%E5%90%8D%E7%A8%B1%E6%8F%8F%E8%BF%B0.png)](http://2.bp.blogspot.com/-sK3GlrDv3cQ/Utybu00xq_I/AAAAAAAAA6g/_omh1Cvm4xA/s1600/08.%E5%90%8D%E7%A8%B1%E6%8F%8F%E8%BF%B0.png)</div>
</div><div>設定好後就完成這個Service，編譯後產生執行檔，接下來就要把這個服務安裝的到作業系統中</div><div>比較正規的作法是去新增一個安裝專案，但為了方便開發起見，以下用批次檔的方式來安裝</div><div>
</div><div>新增幾個批次檔，並改成永遠複製
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-IeOUENSgG7I/Uty35k-diyI/AAAAAAAAA7g/X4PkkxCTMZc/s1600/13.batfile.png)](http://2.bp.blogspot.com/-IeOUENSgG7I/Uty35k-diyI/AAAAAAAAA7g/X4PkkxCTMZc/s1600/13.batfile.png)</div>
<div>install.bat用來安裝 </div><div><pre class="brush:bash">@echo off
set InstallUtil=%WINDIR%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe
if not exist %InstallUtil% set InstallUtil=%WINDIR%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe
if not exist %InstallUtil% set InstallUtil=%WINDIR%\Microsoft.NET\Framework\v3.5\InstallUtil.exe
if not exist %InstallUtil% (
 echo InstallUtil.exe not found
 exit
)

%InstallUtil% -i MyService.exe
</pre></div>
<div>restart.bat用來重新啟動服務 </div><div><pre class="brush:bash">net stop Service1
net start Service1
</pre></div>
<div>start.bat用來啟動服務 </div><div><pre class="brush:bash">net start Service1
</pre></div>
<div>stop.bat用來停止服務 </div><div><pre class="brush:bash">net stop Service1
</pre></div>
<div>uninstall.bat用來反安裝 </div><div><pre class="brush:bash">@echo off
set InstallUtil=%WINDIR%\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe
if not exist %InstallUtil% set InstallUtil=%WINDIR%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe
if not exist %InstallUtil% set InstallUtil=%WINDIR%\Microsoft.NET\Framework\v3.5\InstallUtil.exe
if not exist %InstallUtil% (
 echo InstallUtil.exe not found
 exit
)

%InstallUtil% -u MyService.exe
</pre></div>
<span style="color: red;">注意檔案編碼為ANSI格式</span>，UTF8格式在command pro中執行會有亂碼</div><div>批次檔是透過InstallUtil.exe這個工具程式來安裝和反安裝，詳細的參數請參考[MSDN的說明](http://msdn.microsoft.com/zh-tw/library/50614e95(v=vs.110).aspx)</div><div>
</div><div>點擊install.bat，安裝成功</div><div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-c0GwQkAtsis/Uty3Z7jSevI/AAAAAAAAA7Y/v7dRgrQqiMc/s1600/11.install.png)](http://3.bp.blogspot.com/-c0GwQkAtsis/Uty3Z7jSevI/AAAAAAAAA7Y/v7dRgrQqiMc/s1600/11.install.png)</div>
</div><div>點繫start.bat，啟動服務
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-OuMwHcWUqPA/UtzKFtatI2I/AAAAAAAAA7w/yqZ3XtmwBH8/s1600/14.Start.png)](http://3.bp.blogspot.com/-OuMwHcWUqPA/UtzKFtatI2I/AAAAAAAAA7w/yqZ3XtmwBH8/s1600/14.Start.png)</div>
順利的話就可以在Log2Console中定時收到目前時間
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-6L01sHTG9Ws/UtzKQtBQroI/AAAAAAAAA74/hGzL_CENGSk/s1600/15.run.png)](http://1.bp.blogspot.com/-6L01sHTG9Ws/UtzKQtBQroI/AAAAAAAAA74/hGzL_CENGSk/s1600/15.run.png)</div>

要移除服務就點擊uninstall.bat，反安裝成功</div><div>
</div><div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-D4bFUIA_Kfk/Utyb6S2DsJI/AAAAAAAAA6w/H9_s_cUU95E/s1600/12.uninstall.png)](http://3.bp.blogspot.com/-D4bFUIA_Kfk/Utyb6S2DsJI/AAAAAAAAA6w/H9_s_cUU95E/s1600/12.uninstall.png)</div>
</div><div>
</div><div>
</div>