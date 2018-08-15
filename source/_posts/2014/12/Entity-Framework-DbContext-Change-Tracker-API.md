---
title: Entity Framework DbContext Change Tracker API
tags:
  - DbContext
  - Entity Framework
date: 2014-12-17 18:21:00
---

DbSet有一個Local，是用來存放從資料庫中取得的資料
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new MyInit());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);
                Console.WriteLine(db.Topic.Local.Count);
                db.Topic.Load();
                Console.WriteLine(db.Topic.Local.Count);
            }
        }
    }
}
</pre></div>
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-nFIf_sip55A/VJFaB_gYo0I/AAAAAAAABzs/FxfhAybwr8Q/s1600/01.png)](http://2.bp.blogspot.com/-nFIf_sip55A/VJFaB_gYo0I/AAAAAAAABzs/FxfhAybwr8Q/s1600/01.png)</div>
Local屬性是一個ObservableCollection，可以透過CollectionChanged事件來得到Local集合中發生變化的通知
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new MyInit());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                db.Topic.Local.CollectionChanged += (s, a) =&gt;
                {
                    if (a.NewItems != null)
                    {
                        foreach (Topic item in a.NewItems)
                        {
                            Console.WriteLine("Added:" + item.TopicTitle);
                        }
                    }

                    if (a.OldItems != null)
                    {
                        foreach (Topic item in a.OldItems)
                        {
                            Console.WriteLine("Removed:" + item.TopicTitle);
                        }
                    }
                };

                Topic topic = new Topic { TopicTitle = "abc" };
                db.Topic.Add(topic);
                db.Topic.Remove(topic);
            }
        }
    }
}
</pre></div>
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-SKyRpTru4p4/VJFaB-AddFI/AAAAAAAABzQ/2Yak7QteYlg/s1600/02.png)](http://1.bp.blogspot.com/-SKyRpTru4p4/VJFaB-AddFI/AAAAAAAABzQ/2Yak7QteYlg/s1600/02.png)</div>
當資料取出到DbContext之後，接下來的資料異動會透過EntityState來識別，當呼叫SaveChanges時，執行相對應的SQL處理
Detached: 該實體尚未存在於DbContext中
Unchanged: 該實體剛從資料庫取出或是呼叫過SaveChanges之後，還沒有任何異動
Added: 該實體已經加入到DbContext中，但尚未呼叫SaveChanges
Deleted: 該實體已從DbContext中刪除，但尚未呼叫SaveChanges
Modifyied:該實體已在DbContext中更新過，但尚未調用SaveChanges
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new MyInit());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                // 建立一個新實體，初始狀態會是Detached
                Topic topic = new Topic() { TopicTitle = "abc" };
                Console.WriteLine("{0}, {1}", db.Topic.Local.Count, db.Entry(topic).State);

                // 呼叫Attach可以把資料附加進Local集合中，狀態會是UnChanged
                db.Topic.Attach(topic);
                Console.WriteLine("{0}, {1}", db.Topic.Local.Count, db.Entry(topic).State);

                // 把實體加入DbSet後，狀態會是Added
                db.Topic.Add(topic);
                Console.WriteLine("{0}, {1}", db.Topic.Local.Count, db.Entry(topic).State);

                // 呼叫SaveChanges後，狀態會是UnChanged
                db.SaveChanges();
                Console.WriteLine("{0}, {1}", db.Topic.Local.Count, db.Entry(topic).State);

                // 異動資料後，狀態會是Modified
                topic.TopicTitle = "123";
                Console.WriteLine("{0}, {1}", db.Topic.Local.Count, db.Entry(topic).State);

                // 把實體從DbSet移除後，狀態會是Deleted
                db.Topic.Remove(topic);
                Console.WriteLine("{0}, {1}", db.Topic.Local.Count, db.Entry(topic).State);
            }
        }
    }
}
</pre></div>
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-9aIonFcLz1Y/VJFaB9ZSzbI/AAAAAAAABzM/MehYP1SWpVw/s1600/03.png)](http://1.bp.blogspot.com/-9aIonFcLz1Y/VJFaB9ZSzbI/AAAAAAAABzM/MehYP1SWpVw/s1600/03.png)</div>
除了透過Entry取得實體的狀態外，還可以取得實體不同的值
目前的值(Current Value)
原始的值(Original Value)
資料庫裡面的值(Database Value)
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new MyInit());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                Topic topic = db.Topic.Find(1);
                topic.TopicTitle = "123";
                db.Database.ExecuteSqlCommand("UPDATE Topic SET TopicTitle='456' WHERE TopicID=1");
                Console.WriteLine("CurrentValue:{0}", db.Entry(topic).CurrentValues.GetValue&lt;string&gt;("TopicTitle"));
                Console.WriteLine("OriginalValue:{0}", db.Entry(topic).OriginalValues.GetValue&lt;string&gt;("TopicTitle"));
                Console.WriteLine("DatabaseValue:{0}", db.Entry(topic).GetDatabaseValues().GetValue&lt;string&gt;("TopicTitle"));
            }
        }
    }
}
</pre></div>
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-kRdKg81HKhk/VJFaDLFWQ0I/AAAAAAAABzU/Z9Jsu8pjr-Q/s1600/04.png)](http://4.bp.blogspot.com/-kRdKg81HKhk/VJFaDLFWQ0I/AAAAAAAABzU/Z9Jsu8pjr-Q/s1600/04.png)</div>
如果不想加入Tracker的話，可以呼叫AsNoTracking()即可
<div><pre class="brush:csharp">namespace ConsoleApplication1
{
    using ConsoleApplication1.Models;
    using System;
    using System.Data.Entity;

    class Program
    {
        static void Main(string[] args)
        {
            // 初始化資料庫
            Database.SetInitializer(new MyInit());
            using (DemoContext db = new DemoContext())
            {
                db.Database.Initialize(false);

                Console.WriteLine(db.Topic.Local.Count);
                db.Topic.AsNoTracking().Load();
                Console.WriteLine(db.Topic.Local.Count);
            }
        }
    }
}
</pre></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-IZiN90RhCSk/VJFaD0j1PPI/AAAAAAAABzc/rSOXKf7Kuns/s1600/05.png)](http://4.bp.blogspot.com/-IZiN90RhCSk/VJFaD0j1PPI/AAAAAAAABzc/rSOXKf7Kuns/s1600/05.png)</div>