---
title: Moq 一個用來模擬物件的類別庫
tags:
  - Unit Test
date: 2014-06-03 15:07:00
---

當系統利用介面完成物件來隔離外部物件之後，為了方便測試通常會寫一些假的物件來抽換
但功能越來越多之後，測試的假類別也越多，檔案不好管理
這時後可以讓Moq利用反射的方式讓我們很容易地新增假物件
Moq只能模擬公開的介面，如果是繼承的類別則需要Virtual才能模擬

要使用Moq很簡單，利用NuGet安裝套件就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-cwTzcXKv6l0/U408MjPlOYI/AAAAAAAABXU/yxksMr1XfO8/s1600/01.Moq.png)](http://1.bp.blogspot.com/-cwTzcXKv6l0/U408MjPlOYI/AAAAAAAABXU/yxksMr1XfO8/s1600/01.Moq.png)</div>
用一個簡單的IFoo介面來當例子
<div><pre class="brush:csharp">public interface IFoo
{
    void F1();
    int F2();
    int F3(int x);
    event EventHandler&lt;object&gt; MyEvent;
}
</pre></div>
首先建立一個IFoo型別的Mock物件
在建構式中可以指定MockBehavior來設定模擬物件的程度
Strict是限制需要完整模擬物件，Loose則不需要
預設為Default，也就是Loose
<div><pre class="brush:csharp">private Mock&lt;IFoo&gt; mock;

[TestInitialize]
public void MyTestInitialize()
{
    this.mock = new Mock&lt;IFoo&gt;();
}
</pre></div>
一開始先用沒有回傳值的函式當例子，就先不做更多的設定
直接使用Mock物件的Object屬性取得模擬的假物件就可以使用了
這裡用Verify和Times來檢查該函式的呼叫次數
<div><pre class="brush:csharp">[TestMethod]
public void TestMethod1()
{
    Mock&lt;IFoo&gt; foo = new Mock&lt;IFoo&gt;();
    foo.Object.F1();
    foo.Verify(x =&gt; x.F1(), Times.Once());
}
</pre></div>
再來用一個有回傳值的函式當例子，所以再加上回傳值的設定
這裡的意思是呼叫F2函式的時後，總是回傳123的值回來
<div><pre class="brush:csharp">[TestMethod]
public void TestMethod2()
{
    Mock&lt;IFoo&gt; foo = new Mock&lt;IFoo&gt;();
    foo.Setup(x =&gt; x.F2()).Returns(123);
    Assert.AreEqual(123, foo.Object.F2());
}
</pre></div>
函式中的參數可以透過It物件來設定
這裡的意思是只要傳入int型別的參數，就回傳456的值
<div><pre class="brush:csharp">[TestMethod]
public void TestMethod3()
{
    Mock&lt;IFoo&gt; foo = new Mock&lt;IFoo&gt;();
    foo.Setup(x =&gt; x.F3(It.IsAny&lt;int&gt;())).Returns(456);
    Assert.AreEqual(456, foo.Object.F3(1));
}
</pre></div>
除了回傳值之外，也可以設定Callback函式
<div><pre class="brush:csharp">[TestMethod]
public void TestMethod4()
{
    int counter = 0;
    Mock&lt;IFoo&gt; foo = new Mock&lt;IFoo&gt;();
    foo.Setup(x =&gt; x.F1()).Callback(() =&gt; counter++);
    foo.Object.F1();
    Assert.AreEqual(1, counter);
}
</pre></div>
還有丟回指定的Exception
<div><pre class="brush:csharp">[TestMethod]
[ExpectedException(typeof(Exception))]
public void TestMethod5()
{
    Mock&lt;IFoo&gt; foo = new Mock&lt;IFoo&gt;();
    foo.Setup(x =&gt; x.F1()).Throws(new Exception());
    foo.Object.F1();
}
</pre></div>
還有引發指定的事件
<div><pre class="brush:csharp">[TestMethod]
public void TestMethod6()
{
    Mock&lt;IFoo&gt; foo = new Mock&lt;IFoo&gt;();
    foo.Raise(x =&gt; x.MyEvent += (s, a) =&gt; { Console.WriteLine(a); }, 123);
}
</pre></div>

參考資料
[Moq Quickstart](https://github.com/Moq/moq4/wiki/Quickstart)