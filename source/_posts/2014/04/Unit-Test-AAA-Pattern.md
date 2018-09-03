---
title: Unit Test AAA Pattern
tags:
  - Unit Test
date: 2014-04-28 11:01:00
---
# AAA Pattern

單元測試的程式碼有一個AAA Pattern，就是Arrange Act Assert
主要的目的是要讓測試程式碼好讀、好懂、好維護

* Arrange：初始化測試環境
* Act：執行測試程式
* Assert：驗證測試結果

用一個簡單的程式來說明
主程式

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApplication1
{
    public class Calculator
    {
        public int Add(int x, int y)
        {
            return x + y;
        }
    }
}
```

測試程式
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using ConsoleApplication1;
using Microsoft.VisualStudio.TestTools.UnitTesting;
namespace ConsoleApplication1.Tests
{
    [TestClass()]
    public class CalculatorTests
    {
        [TestMethod()]
        public void AddTest()
        {
            // Arrange
            Calculator calc = new Calculator();
            int x = 1;
            int y = 2;
            int expected = 3;

            // Act
            int actual = calc.Add(x, y);

            // Assert
            Assert.AreEqual(expected, actual);
        }
    }
}
```