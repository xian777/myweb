---
title: Windows Service 遠端偵錯方式
tags:
  - 'C#'
  - windows service
date: 2014-01-20 16:54:00
---

通常在本機開發的時後都是沒有問題的，會發生問題都是佈署到正式環境後才會發生="=
而用一般遠端偵錯的方式，都是已經啟動服務成功才能下中斷點
如果問題出在啟動失敗的話，就中斷不到
這種情境可以加入System.Diagnostics.Debugger.Launch();
讓應用程式等待偵錯工具的連入後才會繼續執行下去
<div><pre class="brush:csharp">using System.ServiceProcess;

namespace MyService
{
    public partial class Service1 : ServiceBase
    {
        private NowTimeReporter reporter = new NowTimeReporter();

        public Service1()
        {
            InitializeComponent();

            // 偵錯中斷用
            System.Diagnostics.Debugger.Launch();
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
執行start.bat來啟動服務
<div><pre class="brush:bash">net start Service1
</pre></div>
就會跳出選擇偵錯工具的畫面，這裡先不選擇
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-M5Yf05_bGOY/UtzipUSGl4I/AAAAAAAAA9s/cJf4tdbcxzU/s1600/05.%E5%81%B5%E9%8C%AF%E5%B7%A5%E5%85%B7.png)](http://4.bp.blogspot.com/-M5Yf05_bGOY/UtzipUSGl4I/AAAAAAAAA9s/cJf4tdbcxzU/s1600/05.%E5%81%B5%E9%8C%AF%E5%B7%A5%E5%85%B7.png)</div>
回到本機，選擇工具-&gt;附加執行緒，選擇遠端和輸入IP，再選擇執行檔，然後附加就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-uGb298oEAvQ/UtzhrLGSTuI/AAAAAAAAA9g/VvbGAN2T-N8/s1600/07.%E9%81%A0%E7%AB%AF%E5%81%B5%E9%8C%AF.png)](http://4.bp.blogspot.com/-uGb298oEAvQ/UtzhrLGSTuI/AAAAAAAAA9g/VvbGAN2T-N8/s1600/07.%E9%81%A0%E7%AB%AF%E5%81%B5%E9%8C%AF.png)</div>
到Server中上放開偵錯工具選擇畫面
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-BusT8ywXWiA/Utzi77WLxFI/AAAAAAAAA90/JnWf7kSvQXs/s1600/08.%E6%94%BE%E9%96%8B.png)](http://2.bp.blogspot.com/-BusT8ywXWiA/Utzi77WLxFI/AAAAAAAAA90/JnWf7kSvQXs/s1600/08.%E6%94%BE%E9%96%8B.png)</div>

就會停在System.Diagnostics.Debugger.Launch();這一行
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-03HYHEc8Wc0/UtzeoQPD90I/AAAAAAAAA9I/0OhDXBJnB4Y/s1600/06.%E4%B8%AD%E6%96%B7.png)](http://3.bp.blogspot.com/-03HYHEc8Wc0/UtzeoQPD90I/AAAAAAAAA9I/0OhDXBJnB4Y/s1600/06.%E4%B8%AD%E6%96%B7.png)</div>
在本機也可以用這種偵錯方式，就不用到應用程式進入點去動手腳
只要讓服務啟動，再選擇偵錯工具連入就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-02isQmXS3aw/UtzkHFl5KlI/AAAAAAAAA-A/g8Jzp4hsUG0/s1600/09.%E6%9C%AC%E6%A9%9F%E5%81%B5%E9%8C%AF.png)](http://2.bp.blogspot.com/-02isQmXS3aw/UtzkHFl5KlI/AAAAAAAAA-A/g8Jzp4hsUG0/s1600/09.%E6%9C%AC%E6%A9%9F%E5%81%B5%E9%8C%AF.png)</div>
<div class="separator" style="clear: both; text-align: center;"></div>