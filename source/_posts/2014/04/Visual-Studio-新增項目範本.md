---
title: Visual Studio 新增項目範本
tags:
  - visual studio
date: 2014-04-09 15:44:00
---

<div>除了專案範本之外，也可以用同樣的方式打包出項目範本 </div><div class="separator" style="clear: both; text-align: center;"></div>先開一個Console專案，沒有特別的原因，只是為了環境簡單而已
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-lr270F-0j9M/U0T4EEiDsRI/AAAAAAAABLM/POKt5GGOQ9k/s1600/01.console%25E5%25B0%2588%25E6%25A1%2588.png)](http://3.bp.blogspot.com/-lr270F-0j9M/U0T4EEiDsRI/AAAAAAAABLM/POKt5GGOQ9k/s1600/01.console%25E5%25B0%2588%25E6%25A1%2588.png)</div>
<div>以最常建立的類別為例</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-0Z_BtrVYON0/U0T4EOj2wTI/AAAAAAAABLU/z0Lu0wRkaEA/s1600/02.%25E6%2596%25B0%25E5%25A2%259E%25E9%25A1%259E%25E5%2588%25A5.png)](http://1.bp.blogspot.com/-0Z_BtrVYON0/U0T4EOj2wTI/AAAAAAAABLU/z0Lu0wRkaEA/s1600/02.%25E6%2596%25B0%25E5%25A2%259E%25E9%25A1%259E%25E5%2588%25A5.png)</div>
<div>修改成適合StyleCop的格式</div>
<div><pre class="brush:csharp">//-----------------------------------------------------------------------
// &lt;copyright file="Class1.cs" company="developer.idv.tw"&gt;
//    Copyright © 2014 developer.idv.tw all rights reserved.
// &lt;/copyright&gt;
//-----------------------------------------------------------------------

namespace ConsoleApplication1
{
    using System;

    /// &lt;summary&gt;
    /// Class1 Class
    /// &lt;/summary&gt;
    public class Class1
    {
        /// &lt;summary&gt;
        /// Initializes a new instance of the &lt;see cref="Class1"/&gt; class
        /// &lt;/summary&gt;
        public Class1()
        {
        }
    }
}
</pre></div>
<div>修改好了一樣選擇左上角的檔案&gt;&gt;匯出範本
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-TyjtiavL1UQ/U0T4ECxMbnI/AAAAAAAABLQ/3Wru9cU50vs/s1600/03.%25E5%258C%25AF%25E5%2587%25BA%25E7%25AF%2584%25E6%259C%25AC.png)](http://2.bp.blogspot.com/-TyjtiavL1UQ/U0T4ECxMbnI/AAAAAAAABLQ/3Wru9cU50vs/s1600/03.%25E5%258C%25AF%25E5%2587%25BA%25E7%25AF%2584%25E6%259C%25AC.png)</div>
</div>
<div>這次選擇匯出項目範本
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-kaNXqcimBag/U0T4EvIX_dI/AAAAAAAABLs/TRt5lU6oFZg/s1600/04.%25E6%2596%25B0%25E5%25A2%259E%25E9%25A0%2585%25E7%259B%25AE%25E7%25AF%2584%25E6%259C%25AC.png)](http://2.bp.blogspot.com/-kaNXqcimBag/U0T4EvIX_dI/AAAAAAAABLs/TRt5lU6oFZg/s1600/04.%25E6%2596%25B0%25E5%25A2%259E%25E9%25A0%2585%25E7%259B%25AE%25E7%25AF%2584%25E6%259C%25AC.png)</div>
</div>
<div>選擇要匯出的檔案範本
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-WSXmUJBP5lQ/U0T4FGTVchI/AAAAAAAABLo/qtv0hcDnvk0/s1600/05.%25E9%2581%25B8%25E6%2593%2587%25E6%25AA%2594%25E6%25A1%2588.png)](http://3.bp.blogspot.com/-WSXmUJBP5lQ/U0T4FGTVchI/AAAAAAAABLo/qtv0hcDnvk0/s1600/05.%25E9%2581%25B8%25E6%2593%2587%25E6%25AA%2594%25E6%25A1%2588.png)</div>
</div>
<div>如果這個項目需要相依於特定元件的話，就要在這裡勾選起來
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-08OwHEx9VpY/U0T4FNid7FI/AAAAAAAABLk/8OZ8WVytVSs/s1600/06.%25E6%2596%25B0%25E5%25A2%259E%25E5%258F%2583%25E8%2580%2583.png)](http://1.bp.blogspot.com/-08OwHEx9VpY/U0T4FNid7FI/AAAAAAAABLk/8OZ8WVytVSs/s1600/06.%25E6%2596%25B0%25E5%25A2%259E%25E5%258F%2583%25E8%2580%2583.png)</div>
</div>
<div>最後輸入這個項目範本的資訊就建立好了
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-GKdkIDkSKtA/U0T4FqHUyOI/AAAAAAAABME/7l95lS9bHnA/s1600/07.%25E5%25AE%258C%25E6%2588%2590%25E9%25A0%2585%25E7%259B%25AE%25E7%25AF%2584%25E6%259C%25AC.png)](http://2.bp.blogspot.com/-GKdkIDkSKtA/U0T4FqHUyOI/AAAAAAAABME/7l95lS9bHnA/s1600/07.%25E5%25AE%258C%25E6%2588%2590%25E9%25A0%2585%25E7%259B%25AE%25E7%25AF%2584%25E6%259C%25AC.png)</div>
</div>
<div>自訂項目範本預設的位置也是在我的文件下面
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-yLbE0GNmy8I/U0T4GGbkU-I/AAAAAAAABMI/V5KC7uPMvqQ/s1600/08.%25E9%25A0%2585%25E7%259B%25AE%25E7%25AF%2584%25E6%259C%25AC%25E8%25B7%25AF%25E5%25BE%2591.png)](http://3.bp.blogspot.com/-yLbE0GNmy8I/U0T4GGbkU-I/AAAAAAAABMI/V5KC7uPMvqQ/s1600/08.%25E9%25A0%2585%25E7%259B%25AE%25E7%25AF%2584%25E6%259C%25AC%25E8%25B7%25AF%25E5%25BE%2591.png)</div>
</div>
<div>新增項目的時後就會看到這個範本
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-SgtNT6SbfbE/U0T4Fz8ATrI/AAAAAAAABL4/ToKQaC73Mjk/s1600/08.%25E6%2596%25B0%25E5%25A2%259E%25E9%25A0%2585%25E7%259B%25AE.png)](http://4.bp.blogspot.com/-SgtNT6SbfbE/U0T4Fz8ATrI/AAAAAAAABL4/ToKQaC73Mjk/s1600/08.%25E6%2596%25B0%25E5%25A2%259E%25E9%25A0%2585%25E7%259B%25AE.png)</div>
</div>
<div>但和預設的範本放在一起不太好找，所以也自訂一個分類來放
到Visual C#資料夾下面新增一個資料夾，名稱就是要自訂的分類名稱
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-jBunqT0cLB4/U0T4G7NX4VI/AAAAAAAABMU/cch8HSWyf1Q/s1600/09.%25E8%2587%25AA%25E8%25A8%2582%25E7%25AF%2584%25E6%259C%25AC%25E8%25B7%25AF%25E5%25BE%2591.png)](http://2.bp.blogspot.com/-jBunqT0cLB4/U0T4G7NX4VI/AAAAAAAABMU/cch8HSWyf1Q/s1600/09.%25E8%2587%25AA%25E8%25A8%2582%25E7%25AF%2584%25E6%259C%25AC%25E8%25B7%25AF%25E5%25BE%2591.png)</div>
</div>
<div>新增項目的時後就會看到自訂的分類了
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-61HfnPxGRE0/U0T4HDhyjNI/AAAAAAAABMM/mv5D9m2sljo/s1600/10.%25E8%2587%25AA%25E8%25A8%2582%25E9%25A1%259E%25E5%2588%25A5.png)](http://4.bp.blogspot.com/-61HfnPxGRE0/U0T4HDhyjNI/AAAAAAAABMM/mv5D9m2sljo/s1600/10.%25E8%2587%25AA%25E8%25A8%2582%25E9%25A1%259E%25E5%2588%25A5.png)</div>
延伸閱讀

[新增專案範本](https://www.blogger.com/goog_1441465540)
[http://blog.developer.idv.tw/2014/04/visual-studio.html](http://blog.developer.idv.tw/2014/04/visual-studio.html)

[新增擴充套件](https://www.blogger.com/goog_1441465545)
[http://blog.developer.idv.tw/2014/04/visual-studio_522.html](http://blog.developer.idv.tw/2014/04/visual-studio_522.html)

參考連結
[http://blog.darkthread.net/post-2012-01-17-vs2010-item-template.aspx](http://blog.darkthread.net/post-2012-01-17-vs2010-item-template.aspx)

[http://msdn.microsoft.com/zh-tw/library/ms247119.aspx](http://msdn.microsoft.com/zh-tw/library/ms247119.aspx)</div>