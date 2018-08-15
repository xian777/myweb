---
title: NLog Database Target
tags:
  - NLog
date: 2014-09-18 13:36:00
---

NLog要把Log存到資料庫的話，可以透過Database這個taget

<div><pre class="brush:xml">&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" autoReload="true"&gt;
    &lt;targets&gt;
        &lt;target xsi:type="Database" name="db"
                connectionString="data source=(localdb)\v11.0;database=LogDB; trusted_connection=true;"
                commandText="INSERT INTO NLog_Error(ThreadId, MachineName, LogName, LogLevel, LogMessage, CallSite, Exception, Stacktrace) VALUES (@ThreadId, @MachineName, @LogName, @LogLevel, @LogMessage, @CallSite, @Exception, @Stacktrace);"&gt;
            &lt;parameter name="@ThreadId" layout="${threadid}"/&gt;
            &lt;parameter name="@MachineName" layout="${machinename}"/&gt;
            &lt;parameter name="@LogName" layout="${logger}"/&gt;
            &lt;parameter name="@LogLevel" layout="${level}"/&gt;
            &lt;parameter name="@LogMessage" layout="${message}"/&gt;
            &lt;parameter name="@CallSite" layout="${callsite:filename=true}"/&gt;
            &lt;parameter name="@Exception" layout="${exception}"/&gt;
            &lt;parameter name="@stacktrace" layout="${stacktrace}"/&gt;
        &lt;/target&gt;
    &lt;/targets&gt;
    &lt;rules&gt;
        &lt;logger name="*" minlevel="Trace" writeTo="db" /&gt;
    &lt;/rules&gt;
&lt;/nlog&gt;</pre></div>

資料庫的Table Schema

<div><pre class="brush:sql">USE LogDB
GO

IF OBJECT_ID('NLog_Error') IS NOT NULL
DROP TABLE NLog_Error
GO

CREATE TABLE NLog_Error
(
 LogId   INT    NOT NULL IDENTITY(1,1) PRIMARY KEY,
 ThreadId  INT    NOT NULL,
 MachineName  VARCHAR(255) NOT NULL,
 LogName   VARCHAR(255) NOT NULL,
 LogLevel  VARCHAR(5)  NOT NULL,
 LogMessage  VARCHAR(MAX) NOT NULL,
 CallSite  VARCHAR(1024) NOT NULL,
 Exception  VARCHAR(1024) NOT NULL,
 Stacktrace  VARCHAR(1024) NOT NULL,
 CreateDateTime DATETIME NOT NULL DEFAULT(GETDATE())
)
GO

</pre></div>