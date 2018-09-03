---
title: IOC 控制反轉 & DI 依賴注入
tags:
  - design pattern
  - Unit Test
date: 2014-05-20 13:55:00
---

# 前言

IOC(Inversion of Control)中文翻譯為控制反轉，是物件導向中的一種設計原則，目的是用來減低物件之間的耦合度
先來看一段兩個物件協同工作的程式碼

```csharp
public class ObjA
{
    private ObjB obj = new ObjB();

    public void SomeAction()
    {
        obj.Work();
    }
}

public class ObjB
{
    public void Work()
    {
        Console.WriteLine("objB Work");
    }
}
```

物件A透過物件B去完成一項工作，所以物件A之中需要明確地指定物件B的存在
也就是說在建立物件A的同時，物件B也同時建立起來了
再簡單一點的說法，沒有物件B就沒有物件A，物件A相依於物件B

這段程式碼如果是萬年不變的邏輯，其實也無所謂
但如果相依的物件需要替換的時後，來看看會發生什麼事

```csharp
public class ObjA
{
    private ObjC obj = new ObjC();

    public void SomeAction()
    {
        obj.Action();
    }
}

public class ObjC
{
    public void Action()
    {
        Console.WriteLine("objC Work");
    }
}
```

宣告的型態要改變，建立物件的類型也要改變，有可能連呼叫的方法都要改變
如果這份程式是自已最近寫的，那可能還會有點印象知道那幾個地方要改
如果一份年久失修又或是別人寫的，那可能需要很有勇氣地用全域取代的方式來修改
所以比較好的設計方式，是針對介面去寫程式

```csharp
public interface IObj
{
    void DoWork();
}

public class ObjA
{
    private IObj obj = new ObjB();

    public void SomeAction()
    {
        obj.DoWork();
    }
}

public class ObjB : IObj
{
    public void DoWork()
    {
        Console.WriteLine("objB Work");
    }
}

public class ObjC : IObj
{
    public void DoWork()
    {
        Console.WriteLine("objC Work");
    }
}
```

這樣的作法在抽換物件的時後，就只要變更建立物件的類型就可以了
但在程式碼中寫死建立的物件類型也是不太好的作法，寫死了就沒有變化性可言
接下來可以配合DI讓程式碼更靈活些

DI(Dependency Injection)中文翻譯為依賴注入，用來將物件相依的關系，利用一些方式從外部注入到物件中，而不必在物件中明確地建立相依物件

# 首先是建構式注入，也是最常用的方式
```csharp
public class ObjA
{
    private IObj obj;

    public void ObjA(IObj obj)
    {
        this.obj = obj;
    }

    public void SomeAction()
    {
        obj.DoWork();
    }
}
```

# 第二種方式是屬性注入，比較適合相依的物件有需要和外部環境互動的時後使用

```csharp
public class ObjA
{
    private IObj obj;

    public IObj Obj 
    {
        get
        {
            return this.obj;
        }
        set
        {
            this.obj = value;
        }
    }

    public void SomeAction()
    {
        if (this.obj == null)
        {
            throw new ArgumentNullException("obj", "obj is null");
        }

        obj.DoWork();
    }
}
```

# 第三種方式是參數注入
```csharp
public class ObjA
{
    public void SomeAction(IObj obj)
    {
        if (obj == null)
        {
            throw new ArgumentNullException("obj", "obj is null");
        }

        obj.DoWork();
    }
}
```