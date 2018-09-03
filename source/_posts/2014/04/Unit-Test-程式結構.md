---
title: Unit Test 程式結構
tags:
  - Unit Test
date: 2014-04-24 16:37:00
---

# 先新增一個測試專案
![測試專案](http://1.bp.blogspot.com/-TqMLm4sU89c/U1jM698OU3I/AAAAAAAABU4/SZc98f6b7kY/s1600/01.%E6%96%B0%E5%A2%9E%E5%B0%88%E6%A1%88.png)](http://1.bp.blogspot.com/-TqMLm4sU89c/U1jM698OU3I/AAAAAAAABU4/SZc98f6b7kY/s1600/01.%E6%96%B0%E5%A2%9E%E5%B0%88%E6%A1%88.png)

# 可以看到主要元件是Microsoft.VisualStudio.QualityTools.UnitTestFramework
![UnitTestFramework](http://4.bp.blogspot.com/-ePU5ykFwprU/U1jM-8lYv-I/AAAAAAAABVA/FjaE9kfddxY/s1600/02.%E6%96%B9%E6%A1%88%E7%B8%BD%E7%AE%A1.png)](http://4.bp.blogspot.com/-ePU5ykFwprU/U1jM-8lYv-I/AAAAAAAABVA/FjaE9kfddxY/s1600/02.%E6%96%B9%E6%A1%88%E7%B8%BD%E7%AE%A1.png)

# 該元件中常用的Attribute如下

| 屬性     |      說明  |
|----------|---------------|
| TestClass    | 用來識別內含測試方法的類別 |
| TestMethod    | 用來識別測試方法，測試方法必須放置在測試類別中 |
| AssemblyInitialize    | 用於該組件所有的測試之前，用來配置此組件所佔用的資源 |
| ClassInitialize    | 用於測試類別的所有測試之前，用來配置該測試類別所使用的資源 |
| TestInitialize    | 用於測試方法執行之前，用來配置該測試方法中所使用的資源 |
| TestCleanup    | 用於測試方法執行完成之後，用來釋放該測試方法所佔用的資源 |
| ClassCleanup    | 用於測試類別中所有的測試完成之後，用來釋放該測試類別所佔用的資源 |
| AssemblyCleanup    | 用於該組件所有測試類別完成測試之後，用來釋放此組件所佔用的資源 |


```csharp
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace UnitTestProject1
{
    [TestClass]
    public class UnitTest1
    {
        [TestClass()]
        public sealed class DivideClassTest
        {
            [AssemblyInitialize()]
            public static void MyAssemblyInitialize(TestContext context)
            {
                Console.WriteLine("MyAssemblyInitialize " + context.TestName);
            }

            [ClassInitialize()]
            public static void MyClassInitialize(TestContext context)
            {
                Console.WriteLine("MyClassInitialize " + context.TestName);
            }

            [TestInitialize()]
            public void MyTestInitialize()
            {
                Console.WriteLine("MyTestInitialize");
            }

            [TestMethod]
            public void TestMethod1()
            {
                Assert.Inconclusive();
            }

            [TestCleanup()]
            public void MyTestCleanup()
            {
                Console.WriteLine("MyTestCleanup");
            }

            [ClassCleanup()]
            public static void MyClassCleanup()
            {
                Console.WriteLine("MyClassCleanup");
            }

            [AssemblyCleanup()]
            public static void MyAssemblyCleanup()
            {
                Console.WriteLine("MyAssemblyCleanup");
            }
        }
    }
}
```