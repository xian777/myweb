---
title: NLog Mail Target
tags:
  - NLog
date: 2012-12-31 01:07:00
---

## NLog Mail Target
<div>透過郵件把Log寄出，例如Error和Fatal等級的Log可以考慮直接寄出給管理員</div>

## 屬性
<div>完整的資料請參考[官網Mail Target文件](https://github.com/nlog/nlog/wiki/Mail-target)</div><div>
</div><div>

*   html - 是否為HTML格式的郵件，預設為false
*   encoding - 郵件編碼，預設為UTF8
*   subject - 郵件主題
*   to - 收件者
*   bcc - 密件副本
*   cc - 副本
*   from - 寄件者
*   body - 郵件內容，預設為${message}
*   smtpUserName - 郵件主機寄信帳號
*   enableSsl - 是否啟用SSL通訊協定
*   smtpPassword - 郵件主密寄信密碼
*   smtpAuthentication - 郵件主機驗證模組，Basci、None、Ntml，預設為None
*   smtpServer - &nbsp;郵件主機位址
*   smtpPort - 郵件主機埠號，預設為25</div><div>
</div><div>一個簡單的範例，發生Error層級以上的Log，就寄信給管理員</div><div><pre class="brush:csharp">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"&gt;

    &lt;!-- 
  See http://nlog-project.org/wiki/Configuration_file 
  for information on customizing logging rules and outputs.
   --&gt;
    &lt;targets&gt;
        &lt;target xsi:type="Mail" name="MailAlarm" 
                smtpServer="郵件主機位置"
                smtpPort="25"
                subject="${machineName}於${longdate}發生問題"
                from="寄信人Mail"
                to="收信人Mail"
                body="${longdate} ${uppercase:${level}} ${message}" /&gt;
    &lt;/targets&gt;
    &lt;rules&gt;
        &lt;logger name="*" minlevel="Error" writeTo="MailAlarm" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;
</pre></div>