---
title: AutoMapper 自訂對應關系
tags:
  - AutoMapper
date: 2014-08-05 18:18:00
---

<div>在來源和目的物件中，如果屬性名稱和型態都相同的話，AutoMapper會自動轉換
但通常事情不會這麼單純，很多時後我們會需要指定轉換的方式，用一個簡單的例子來說明</div>
<div>首先是來源的Model物件</div><div><pre class="brush:csharp">public class DemoModel
{
    public int CustId { get; set; }
    public string CustName { get; set; }
    public bool CustGender { get; set; }
}
</pre></div>
<div>再來是要轉換的ViewModel物件</div><div><pre class="brush:csharp">public class DemoViewModel
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string FullName { get; set; }
    public string Gender { get; set; }
    public DateTime Date { get; set; }
}
</pre></div>
<div>轉換的設定方式
Ignore是用來略過對應，不給值
MapFrom是用來指定對應的屬性名稱，或是組合多個屬性值
ResolveUsing是指定自訂的型別轉換方式
UseValue是在轉換的過程中直接給值
NullSubstitute是在原始值為空的時後才給值
Condition傳入一個條件為true才給值</div><div><pre class="brush:csharp">public class Class1
{
    public void GetViewModel()
    {
        Mapper.CreateMap&lt;DemoModel, DemoViewModel&gt;()
            .ForMember(dest =&gt; dest.Id, opt =&gt; opt.Ignore())
            .ForMember(dest =&gt; dest.Name, opt =&gt; opt.MapFrom(src =&gt; src.CustName))
            .ForMember(dest =&gt; dest.FullName, opt =&gt; opt.MapFrom(src =&gt; string.Format("{0}:{1}", src.CustId, src.CustName)))
            .ForMember(dest =&gt; dest.Gender, opt =&gt; opt.ResolveUsing&lt;GenderResolver&gt;().FromMember(src =&gt; src.CustGender))
            .ForMember(dest =&gt; dest.Date, opt =&gt; opt.UseValue&lt;DateTime&gt;(DateTime.Now));

        DemoModel model = new DemoModel
        {
            CustId = 123,
            CustName = "abc",
            CustGender = true
        };

        DemoViewModel viewModel = Mapper.Map&lt;DemoModel, DemoViewModel&gt;(model);
        Console.WriteLine("id:{0}, name:{1}, fullname:{2}, gender:{3}, date:{4}", viewModel.Id, viewModel.Name, viewModel.FullName, viewModel.Date, viewModel.Gender);
    }

    private class GenderResolver : ValueResolver&lt;bool, string&gt;
    {
        protected override string ResolveCore(bool source)
        {
            return source ? "男" : "女";
        }
    }
}
</pre></div>