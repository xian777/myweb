---
title: Controller加入單元測試
tags:
  - Unit Test
date: 2014-06-04 11:43:00
---
# 前言

前面介紹過Repository Pattern用來隔離資料庫，和Autoface注入介面，接下來可以在Controller中寫一些測試項目來驗證流程正確與否

# 首先加入一個測試專案，名稱為要測試的專案名稱後面加.Tests
![加入一個測試專案](http://1.bp.blogspot.com/-OZinuFI1mHU/U46Vkhkz8aI/AAAAAAAABX8/jcka12CXCac/s1600/01.%E9%96%8B%E6%96%B0%E5%B0%88%E6%A1%88.png)

# 依照MVC的習慣，加入一個Controllers資料夾
在資料夾下新增一個單元測試檔案，名稱為要測試的控制器名稱後面加Test
![加入一個Controllers資料夾](http://4.bp.blogspot.com/-pYXbFulua7o/U46VpOARWdI/AAAAAAAABYE/KVYnuvxFJ4M/s1600/02.%E6%96%B0%E5%A2%9E%E5%96%AE%E5%85%83%E6%B8%AC%E8%A9%A6.png)

# 首先初始化一些要共用的變數
```csharp
private Mock<IGuestbookRepository> repository;
private GuestbookController ctrl;

[TestInitialize]
public void GuestbookControllerTestInitialize()
{
    this.repository = new Mock<IGuestbookRepository>();
    this.repository
        .Setup(x => x.Find(It.IsIn<int>(1)))
        .Returns(new Guestbook());
    this.ctrl = new GuestbookController(this.repository.Object);
}
```

# Index相關測試
```csharp
[TestMethod]
public void Index_GET_Return_ViewResult()
{
    var view = this.ctrl.Index() as ViewResult;
    Assert.IsNotNull(view);
}
```

# Create相關測試
```csharp
[TestMethod]
public void Create_GET_Return_ViewResult()
{
    var view = this.ctrl.Create() as ViewResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Create_POST_Success_Return_RedirectToRouteResult()
{
    var model = new Guestbook();
    var view = this.ctrl.Create(model) as RedirectToRouteResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Create_POST_Fail_Return_ViewResult()
{
    var model = new Guestbook();
    this.ctrl.ModelState.AddModelError("key", "message");
    var view = this.ctrl.Create(model) as ViewResult;
    Assert.IsNotNull(view);
}
```

# Edit相關測試
```csharp
[TestMethod]
public void Edit_GET_Null_ID_Return_HttpStatusCodeResult()
{
    int? id = null;
    var view = this.ctrl.Edit(id) as HttpStatusCodeResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Edit_GET_Invalid_ID_Return_HttpNotFoundResult()
{
    int id = 0;
    var view = this.ctrl.Edit(id) as HttpNotFoundResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Edit_GET_Valid_ID_Return_ViewResult()
{
    int id = 1;
    var view = this.ctrl.Edit(id) as ViewResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Edit_POST_Success_Return_RedirectToRouteResult()
{
    var model = new Guestbook();
    var view = this.ctrl.Edit(model) as RedirectToRouteResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Edit_POST_Fail_Return_ViewResult()
{
    var model = new Guestbook();
    this.ctrl.ModelState.AddModelError("key", "message");
    var view = this.ctrl.Edit(model) as ViewResult;
    Assert.IsNotNull(view);
}
```

# Delete相關測試
```csharp
[TestMethod]
public void Delete_GET_Null_ID_Return_HttpStatusCodeResult()
{
    int? id = null;
    var view = this.ctrl.Delete(id) as HttpStatusCodeResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Delete_GET_Invalid_ID_Return_HttpNotFound()
{
    int? id = 0;
    var view = this.ctrl.Delete(id) as HttpNotFoundResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Delete_GET_Valid_ID_Return_ViewResult()
{
    int? id = 1;
    var view = this.ctrl.Delete(id) as ViewResult;
    Assert.IsNotNull(view);
}

[TestMethod]
public void Delete_POST_Return_RedirectToRouteResult()
{
    int id = 1;
    var view = this.ctrl.DeleteConfirmed(id) as RedirectToRouteResult;
    Assert.IsNotNull(view);
}
```

# 單元測試涵蓋率可以參考NCover、NCrunch等工具