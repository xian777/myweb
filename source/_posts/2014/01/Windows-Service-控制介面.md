---
title: Windows Service 控制介面
tags:
  - 'C#'
  - windows service
date: 2014-01-20 18:52:00
---

[ServiceController](http://msdn.microsoft.com/zh-tw/library/system.serviceprocess.servicecontroller(v=vs.110).aspx)這個類別可以用來控制Service的狀態
詳細的資訊請參考[MSDN上面的文件](http://msdn.microsoft.com/zh-tw/library/system.serviceprocess.servicecontroller(v=vs.110).aspx)

新增一個Windows Form應用程式來當範例
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-9Zaajyh2xjg/Utz6R411nDI/AAAAAAAAA_c/OENaeRnmfCQ/s1600/01.%E6%96%B0%E5%B0%88%E6%A1%88.png)](http://1.bp.blogspot.com/-9Zaajyh2xjg/Utz6R411nDI/AAAAAAAAA_c/OENaeRnmfCQ/s1600/01.%E6%96%B0%E5%B0%88%E6%A1%88.png)</div>
首先要先參考System.ServiceProcess這個元件
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-6sDG8aGMtxo/Utz6eAxax9I/AAAAAAAAA_k/-aidHLl07JQ/s1600/02.ServiceProcess.png)](http://3.bp.blogspot.com/-6sDG8aGMtxo/Utz6eAxax9I/AAAAAAAAA_k/-aidHLl07JQ/s1600/02.ServiceProcess.png)</div>
簡單拉兩個按鈕來控制啟動或停止服務
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-e7Ashr3npdo/Utz-zlUNARI/AAAAAAAAA_w/_XQ09xrhLi8/s1600/03.%E6%8C%89%E9%88%95.png)](http://4.bp.blogspot.com/-e7Ashr3npdo/Utz-zlUNARI/AAAAAAAAA_w/_XQ09xrhLi8/s1600/03.%E6%8C%89%E9%88%95.png)</div>
在Button Click事件中，透過ServiceController來切換狀態
<div><pre class="brush:csharp">private void Btn_Start_Click(object sender, EventArgs e)
{
    // 設定服務
    using (ServiceController objSC = new ServiceController("Service1"))
    {
        // 設定一個 Timeout 時間，若超過 30 秒啟動不成功就宣告失敗
        TimeSpan timeout = TimeSpan.FromMilliseconds(1000 * 30);

        // 啟動服務
        objSC.Start();

        // 設定該服務必須在timeout時間內切換到Running狀態
        objSC.WaitForStatus(ServiceControllerStatus.Running, timeout);
    }
}

private void Btn_Stop_Click(object sender, EventArgs e)
{
    // 設定服務
    using (ServiceController objSC = new ServiceController("Service1"))
    {
        // 若該服務不是「停用」的狀態，才將其停止運作，否則會引發 Exception  
        if (objSC.Status != ServiceControllerStatus.Stopped &amp;&amp; objSC.Status != ServiceControllerStatus.StopPending)
        {
            // 設定一個 Timeout 時間，若超過30秒停止不成功就宣告失敗!  
            TimeSpan timeout = TimeSpan.FromMilliseconds(1000 * 30);

            // 停止服務
            objSC.Stop();

            // 設定該服務必須在timeout時間內切換到Stopped狀態
            objSC.WaitForStatus(ServiceControllerStatus.Stopped, timeout);
        }
    }
}
</pre></div>
再拉個按鈕來發送自訂命令
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-J0zJAuvlOIc/Utz_J-xZXrI/AAAAAAAAA_4/h5dhVxRDgtA/s1600/04.%E8%87%AA%E8%A8%82%E5%91%BD%E4%BB%A4%E6%8C%89%E9%88%95.png)](http://4.bp.blogspot.com/-J0zJAuvlOIc/Utz_J-xZXrI/AAAAAAAAA_4/h5dhVxRDgtA/s1600/04.%E8%87%AA%E8%A8%82%E5%91%BD%E4%BB%A4%E6%8C%89%E9%88%95.png)</div>
透過ExecuteCommand來發送命令，<span style="color: red;">需要注意這裡面的CommandID必須在128~256這個範圍</span>
<div><pre class="brush:csharp">private void Btn_CMD_128_Click(object sender, EventArgs e)
{
    // 設定服務
    using (ServiceController objSC = new ServiceController("Service1"))
    {
        if (objSC.Status == ServiceControllerStatus.Running)
        {
            objSC.ExecuteCommand(128);
        }
    }
}
</pre></div>
在Service中去覆寫OnCustomCommand，就可以收到發送命令的通知
至於收到什麼編號要去做什麼行為，簡單地用個switch case就行了
<div><pre class="brush:csharp">protected override void OnCustomCommand(int command)
{
    switch (command)
    {
        case 128:
            break;
        case 129:
            break;
        case 130:
            break;
        default:
            break;
    }
}
</pre></div>