---
title: Windows Service 本機偵錯方式
tags:
  - 'C#'
  - windows service
date: 2014-01-20 16:02:00
---

Windows Service輸出類型雖然是Windows 應用程式
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-gYEQnP9vcX0/UtzUoK5OSuI/AAAAAAAAA8I/CG9AE2X77G0/s1600/01.%E5%B0%88%E6%A1%88%E9%A1%9E%E5%9E%8B.png)](http://2.bp.blogspot.com/-gYEQnP9vcX0/UtzUoK5OSuI/AAAAAAAAA8I/CG9AE2X77G0/s1600/01.%E5%B0%88%E6%A1%88%E9%A1%9E%E5%9E%8B.png)</div>
但開發的時後直接執行卻會出現啟動錯誤的提示訊息
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-k-LwIRVhZpI/UtzUsdZe7DI/AAAAAAAAA8Q/TzHsZQQvEvI/s1600/02.%E5%95%9F%E5%8B%95%E9%8C%AF%E8%AA%A4.png)](http://3.bp.blogspot.com/-k-LwIRVhZpI/UtzUsdZe7DI/AAAAAAAAA8Q/TzHsZQQvEvI/s1600/02.%E5%95%9F%E5%8B%95%E9%8C%AF%E8%AA%A4.png)</div>
原因在於程式進入點是用ServiceBase來啟動，而不是Application.Run
<div><pre class="brush:csharp">using System.ServiceProcess;

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
</pre></div>
為了方便本機開發，就需要先動點手腳
首先先把邏輯拆到獨立的類別去，並公開Start和Stop方法
<div><pre class="brush:csharp">using System;
using System.Timers;
using Common.Logging;

namespace MyService
{
    internal class NowTimeReporter
    {
        private Timer timer;
        private ILog log;
        private double timerInterval = 1000;
        private string datetimeFormat = "yyyy/MM/dd HH:mm:ss";

        public NowTimeReporter()
        {
            this.log = LogManager.GetLogger(typeof(Service1));
            this.timer = new Timer();
            this.timer.Interval = this.timerInterval;
            this.timer.AutoReset = false;
            this.timer.Enabled = false;
            this.timer.Elapsed += Timer_Elapsed;
        }

        public void Start()
        {
            this.timer.Enabled = true;
        }

        public void Stop()
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
</pre></div>

讓Service只是簡單的呼叫Start和Stop
<div><pre class="brush:csharp">using System.ServiceProcess;

namespace MyService
{
    public partial class Service1 : ServiceBase
    {
        private NowTimeReporter reporter = new NowTimeReporter();

        public Service1()
        {
            InitializeComponent();
        }

        protected override void OnStart(string[] args)
        {
            this.reporter.Start();
        }

        protected override void OnStop()
        {
            this.reporter.Stop();
        }
    }
}
</pre></div>
把專案類型切換成主控台應用程式
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-_6dwZbrHQ6k/UtzVxS49o9I/AAAAAAAAA8c/7ZwqsjwMIz8/s1600/03.%E4%B8%BB%E6%8E%A7%E5%8F%B0%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F.png)](http://4.bp.blogspot.com/-_6dwZbrHQ6k/UtzVxS49o9I/AAAAAAAAA8c/7ZwqsjwMIz8/s1600/03.%E4%B8%BB%E6%8E%A7%E5%8F%B0%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F.png)</div>

接下來在程式進入點的地方利用執行時的使用者名稱來判斷要用那一種方式啟動
<div><pre class="brush:csharp">using System;
using System.ServiceProcess;

namespace MyService
{
    static class Program
    {
        /// &lt;summary&gt;
        /// 應用程式的主要進入點。
        /// &lt;/summary&gt;
        static void Main()
        {
            if (Environment.UserName == "SYSTEM")
            {
                ServiceBase[] ServicesToRun;
                ServicesToRun = new ServiceBase[] 
                { 
                    new Service1() 
                };
                ServiceBase.Run(ServicesToRun);
            }
            else
            {
                NowTimeReporter reporter = new NowTimeReporter();
                reporter.Start();
                Console.ReadLine();
            }
        }
    }
}
</pre></div>
然後在本機開發的時後，就可以直接下中斷點了
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-1IvUKb9mbqg/UtzX2QkWC2I/AAAAAAAAA8w/MlS2NUEZBXU/s1600/04.%E4%B8%AD%E6%96%B7%E9%BB%9E.png)](http://1.bp.blogspot.com/-1IvUKb9mbqg/UtzX2QkWC2I/AAAAAAAAA8w/MlS2NUEZBXU/s1600/04.%E4%B8%AD%E6%96%B7%E9%BB%9E.png)</div>