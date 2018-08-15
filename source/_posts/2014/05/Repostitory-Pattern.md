---
title: Repostitory Pattern
tags:
  - design pattern
date: 2014-05-28 18:12:00
---

Repository Pattern 是一個用來切割資料存取層和商業邏輯層的模式
針對資料的存取提供了基本的新增、修改、刪除、查詢等操作
返回的對象應該為IQueryable以供商業邏輯做更進一步的處理
這樣的好處是商業邏輯不直接處理資料的存取，方便之後抽換資料存取層，也方便單元測試
以下用一個簡單的留言版當例子透過ADO.NET和Entity Framework來存取資料
首先準備好留言版的資料庫，資料表就簡單的用GuestbookId和Message就好
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-NkgUfftgZso/U4Wx3J8w7QI/AAAAAAAABW0/3iDzzqb62zA/s1600/01.DB.png)](http://3.bp.blogspot.com/-NkgUfftgZso/U4Wx3J8w7QI/AAAAAAAABW0/3iDzzqb62zA/s1600/01.DB.png)</div>
定義一個Guestbook的Entity
<pre class="brush:csharp">namespace WebApplication1.Models
{
    using System.ComponentModel.DataAnnotations;
    using System.ComponentModel.DataAnnotations.Schema;

    [Table("Guestbook")]
    public class Guestbook
    {
        [Key]
        public int GuestbookId { get; set; }
        public string Message { get; set; }
    }
}
</pre>
順便定義一個DbContext
<pre class="brush:csharp">namespace WebApplication1.Models
{
    using System.Data.Entity;

    public class GuestbookContext : DbContext
    {
        public DbSet&lt;Guestbook&gt; Guestbook { get; set; }
    }
}
</pre>
定義一個IGuestbookRepository介面
<pre class="brush:csharp">namespace WebApplication1.Repositories
{
    using System;
    using System.Linq;
    using WebApplication1.Models;

    public interface IGuestbookRepository : IDisposable
    {
        IQueryable&lt;Guestbook&gt; GetAll();
        Guestbook Find(int id);
        void Add(Guestbook model);
        void Edit(Guestbook model);
        void Delete(int id);
    }
}
</pre>
透過EntityFramework實作一個Repository
<pre class="brush:csharp">namespace WebApplication1.Repositories
{
    using System;
    using System.Data.Entity;
    using System.Linq;
    using WebApplication1.Models;

    public class EFGuestbookRepository : IGuestbookRepository
    {
        private bool disposed = false;
        private GuestbookContext db;

        public EFGuestbookRepository()
        {
            this.db = new GuestbookContext();
        }

        public IQueryable&lt;Guestbook&gt; GetAll()
        {
            return this.db.Guestbook;
        }

        public Models.Guestbook Find(int id)
        {
            return this.db.Guestbook.Find(id);
        }

        public void Add(Guestbook model)
        {
            this.db.Guestbook.Add(model);
            this.db.SaveChanges();
        }

        public void Edit(Guestbook model)
        {
            this.db.Entry(model).State = EntityState.Modified;
            this.db.SaveChanges();
        }

        public void Delete(int id)
        {
            var model = new Guestbook { GuestbookId = id };
            this.db.Entry(model).State = EntityState.Deleted;
            this.db.SaveChanges();
        }

        public void Dispose()
        {
            this.Dispose(true);
            GC.SuppressFinalize(this);
        }

        private void Dispose(bool disposing)
        {
            if (disposed)
            {
                return;
            }

            this.disposed = true;

            if (disposing)
            {
                this.db.Dispose();
            }
        }
    }
}
</pre>
透過ADO.Net實作一個Repository
<pre class="brush:csharp">namespace WebApplication1.Repositories
{
    using System;
    using System.Collections.Generic;
    using System.Configuration;
    using System.Data;
    using System.Data.SqlClient;
    using System.Linq;
    using WebApplication1.Models;

    public class ADONetGuestbookRepository : IGuestbookRepository
    {
        private bool disposed = false;
        private SqlConnection objConn;
        private SqlCommand objCmd;

        public ADONetGuestbookRepository()
        {
            string strConn = ConfigurationManager.ConnectionStrings["GuestbookContext"].ConnectionString;
            objConn = new SqlConnection(strConn);
            objConn.Open();
            objCmd = new SqlCommand();
            objCmd.Connection = objConn;
        }

        public IQueryable&lt;Guestbook&gt; GetAll()
        {
            List&lt;Guestbook&gt; list = new List&lt;Guestbook&gt;();
            objCmd.CommandText = "SELECT * FROM Guestbook";
            using (SqlDataReader objDtr = objCmd.ExecuteReader())
            {
                while (objDtr.Read())
                {
                    Guestbook model = new Guestbook()
                    {
                        GuestbookId = Convert.ToInt32(objDtr["GuestbookId"]),
                        Message = objDtr["Message"].ToString(),
                    };

                    list.Add(model);
                }
            }

            return list.AsQueryable();
        }

        public Models.Guestbook Find(int id)
        {
            Guestbook model = new Guestbook();
            objCmd.CommandText = "SELECT * FROM Guestbook WHERE GuestbookId = @GuestbookId";
            objCmd.Parameters.AddWithValue("@GuestbookId", id);
            using (SqlDataReader objDtr = objCmd.ExecuteReader())
            {
                if (objDtr.Read())
                {
                    model.GuestbookId = Convert.ToInt32(objDtr["GuestbookId"]);
                    model.Message = objDtr["Message"].ToString();
                }
            }

            return model;
        }

        public void Add(Guestbook model)
        {
            objCmd.CommandText = "INSERT INTO Guestbook(Message) VALUES(@Message)";
            objCmd.Parameters.AddWithValue("@Message", model.Message);
            objCmd.ExecuteNonQuery();
        }

        public void Edit(Guestbook model)
        {
            objCmd.CommandText = "UPDATE Guestbook SET Message = @Message WHERE GuestbookId = @GuestbookId";
            objCmd.Parameters.AddWithValue("@GuestbookId", model.GuestbookId);
            objCmd.Parameters.AddWithValue("@Message", model.Message);
            objCmd.ExecuteNonQuery();
        }

        public void Delete(int id)
        {
            objCmd.CommandText = "DELETE FROM Guestbook WHERE GuestbookId = @GuestbookId";
            objCmd.Parameters.AddWithValue("@GuestbookId", id);
            objCmd.ExecuteNonQuery();
        }

        public void Dispose()
        {
            this.Dispose(true);
            GC.SuppressFinalize(this);
        }

        protected virtual void Dispose(bool disposing)
        {
            if (this.disposed)
            {
                return;
            }

            this.disposed = true;

            if (disposing)
            {
                if (objConn.State != ConnectionState.Closed)
                {
                    objConn.Close();
                }

                this.objConn.Dispose();
                this.objCmd.Dispose();
            }
        }
    }
}
</pre>
透過Scaffold產生Controller和View
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-SafCT7TfyIg/U4WyQiQuM2I/AAAAAAAABW8/fguKz0kphZg/s1600/02.scaffold.png)](http://4.bp.blogspot.com/-SafCT7TfyIg/U4WyQiQuM2I/AAAAAAAABW8/fguKz0kphZg/s1600/02.scaffold.png)</div>
加入控制器
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-hPJxj_kG7P8/U4WyZBpJshI/AAAAAAAABXE/JNLg-kwM4Bw/s1600/03.%E5%8A%A0%E5%85%A5%E6%8E%A7%E5%88%B6%E5%99%A8.png)](http://3.bp.blogspot.com/-hPJxj_kG7P8/U4WyZBpJshI/AAAAAAAABXE/JNLg-kwM4Bw/s1600/03.%E5%8A%A0%E5%85%A5%E6%8E%A7%E5%88%B6%E5%99%A8.png)</div>

產生的Controller裡面是直接透過Entity Framework存取資料
<pre class="brush:csharp">using System;
using System.Collections.Generic;
using System.Data;
using System.Data.Entity;
using System.Linq;
using System.Net;
using System.Web;
using System.Web.Mvc;
using WebApplication1.Models;

namespace WebApplication1.Controllers
{
    public class GuestbookController : Controller
    {
        private GuestbookContext db = new GuestbookContext();

        // GET: Guestbook
        public ActionResult Index()
        {
            return View(db.Guestbook.ToList());
        }

        // GET: Guestbook/Details/5
        public ActionResult Details(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Guestbook guestbook = db.Guestbook.Find(id);
            if (guestbook == null)
            {
                return HttpNotFound();
            }
            return View(guestbook);
        }

        // GET: Guestbook/Create
        public ActionResult Create()
        {
            return View();
        }

        // POST: Guestbook/Create
        // 若要免於過量張貼攻擊，請啟用想要繫結的特定屬性，如需
        // 詳細資訊，請參閱 http://go.microsoft.com/fwlink/?LinkId=317598。
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Create([Bind(Include = "GuestbookId,Message")] Guestbook guestbook)
        {
            if (ModelState.IsValid)
            {
                db.Guestbook.Add(guestbook);
                db.SaveChanges();
                return RedirectToAction("Index");
            }

            return View(guestbook);
        }

        // GET: Guestbook/Edit/5
        public ActionResult Edit(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Guestbook guestbook = db.Guestbook.Find(id);
            if (guestbook == null)
            {
                return HttpNotFound();
            }
            return View(guestbook);
        }

        // POST: Guestbook/Edit/5
        // 若要免於過量張貼攻擊，請啟用想要繫結的特定屬性，如需
        // 詳細資訊，請參閱 http://go.microsoft.com/fwlink/?LinkId=317598。
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Edit([Bind(Include = "GuestbookId,Message")] Guestbook guestbook)
        {
            if (ModelState.IsValid)
            {
                db.Entry(guestbook).State = EntityState.Modified;
                db.SaveChanges();
                return RedirectToAction("Index");
            }
            return View(guestbook);
        }

        // GET: Guestbook/Delete/5
        public ActionResult Delete(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Guestbook guestbook = db.Guestbook.Find(id);
            if (guestbook == null)
            {
                return HttpNotFound();
            }
            return View(guestbook);
        }

        // POST: Guestbook/Delete/5
        [HttpPost, ActionName("Delete")]
        [ValidateAntiForgeryToken]
        public ActionResult DeleteConfirmed(int id)
        {
            Guestbook guestbook = db.Guestbook.Find(id);
            db.Guestbook.Remove(guestbook);
            db.SaveChanges();
            return RedirectToAction("Index");
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
}

</pre>做一點調整改用剛定義的IGuestbookRepository介面來存取資料
<pre class="brush:csharp">using System;
using System.Collections.Generic;
using System.Data;
using System.Data.Entity;
using System.Linq;
using System.Net;
using System.Web;
using System.Web.Mvc;
using WebApplication1.Models;
using WebApplication1.Repositories;

namespace WebApplication1.Controllers
{
    public class GuestbookController : Controller
    {
        private IGuestbookRepository db;

        public GuestbookController()
        {
            this.db = new EFGuestbookRepository();
        }

        // GET: Guestbook
        public ActionResult Index()
        {
            return View(this.db.GetAll());
        }

        // GET: Guestbook/Details/5
        public ActionResult Details(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Guestbook guestbook = this.db.Find(id.Value);
            if (guestbook == null)
            {
                return HttpNotFound();
            }
            return View(guestbook);
        }

        // GET: Guestbook/Create
        public ActionResult Create()
        {
            return View();
        }

        // POST: Guestbook/Create
        // 若要免於過量張貼攻擊，請啟用想要繫結的特定屬性，如需
        // 詳細資訊，請參閱 http://go.microsoft.com/fwlink/?LinkId=317598。
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Create([Bind(Include = "GuestbookId,Message")] Guestbook guestbook)
        {
            if (ModelState.IsValid)
            {
                this.db.Add(guestbook);
                return RedirectToAction("Index");
            }

            return View(guestbook);
        }

        // GET: Guestbook/Edit/5
        public ActionResult Edit(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Guestbook guestbook = this.db.Find(id.Value);
            if (guestbook == null)
            {
                return HttpNotFound();
            }
            return View(guestbook);
        }

        // POST: Guestbook/Edit/5
        // 若要免於過量張貼攻擊，請啟用想要繫結的特定屬性，如需
        // 詳細資訊，請參閱 http://go.microsoft.com/fwlink/?LinkId=317598。
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Edit([Bind(Include = "GuestbookId,Message")] Guestbook guestbook)
        {
            if (ModelState.IsValid)
            {
                this.db.Edit(guestbook);
                return RedirectToAction("Index");
            }
            return View(guestbook);
        }

        // GET: Guestbook/Delete/5
        public ActionResult Delete(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Guestbook guestbook = this.db.Find(id.Value);
            if (guestbook == null)
            {
                return HttpNotFound();
            }
            return View(guestbook);
        }

        // POST: Guestbook/Delete/5
        [HttpPost, ActionName("Delete")]
        [ValidateAntiForgeryToken]
        public ActionResult DeleteConfirmed(int id)
        {
            this.db.Delete(id);
            return RedirectToAction("Index");
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
}

</pre>要切換存取資料的Repository只要在建構式中切換建立的類別就行了
<pre class="brush:csharp">public GuestbookController()
{
    // this.db = new EFGuestbookRepository();
    this.db = new ADONetGuestbookRepository();
}
</pre>
透過DI的方式注入介面切換就更靈活了
<pre class="brush:csharp">public GuestbookController(IGuestbookRepository repository)
{
    this.db = repository;
}
</pre>
參考資料
[IOC 控制反轉 &amp; DI 依賴注入](http://blog.developer.idv.tw/2014/05/ioc-di.html)
[Autofac 一種IOC容器](http://blog.developer.idv.tw/2014/06/autofac-ioc.html)