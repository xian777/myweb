---
title: 'C# 排程套件: Quartz'
tags:
  - NuGet套件
date: 2016-05-23 17:06:00
---

# Quartz 套件

## 簡介
Quartz是個排程套件

## 安裝
```shell
$ install-package Quartz
```

## 建立Job
```csharp
namespace ConsoleApplication1
{
&nbsp; &nbsp; using System;
&nbsp; &nbsp; using Quartz;

&nbsp; &nbsp; [DisallowConcurrentExecution]
&nbsp; &nbsp; internal class MyJob : IJob
&nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; public void Execute(IJobExecutionContext context)
&nbsp; &nbsp; &nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Console.WriteLine("do job");
&nbsp; &nbsp; &nbsp; &nbsp; }
&nbsp; &nbsp; }
}
```
## 建立排程
```csharp
namespace ConsoleApplication1
{
&nbsp; &nbsp; using Quartz;
&nbsp; &nbsp; using Quartz.Impl;

&nbsp; &nbsp; internal class Program
&nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; private static void Main(string[] args)
&nbsp; &nbsp; &nbsp; &nbsp; {
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // 建立排程器
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var schedulerFactory = new StdSchedulerFactory();
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var schedular = schedulerFactory.GetScheduler();

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // 建立Job
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; IJobDetail job = JobBuilder.Create&lt;MyJob&gt;()
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .WithIdentity("MyJob")
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .Build();

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // 建立Trigger
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ITrigger trigger = TriggerBuilder.Create()
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .WithCronSchedule("0 0/1 * * * ?")
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .WithIdentity("MyJobTrigger")
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; .Build();

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // Job配對Trigger
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; schedular.ScheduleJob(job, trigger);

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // 啟動排程器
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; schedular.Start();
&nbsp; &nbsp; &nbsp; &nbsp; }
&nbsp; &nbsp; }
}
```

## 注意事項
* 排程是固定周期觸發，和Job的執行時間無關
* 每次觸發都會重新建立一個全新的Job物件
* 在Job上加入DisallowConcurrentExecution來限制每次只能執行一個Job