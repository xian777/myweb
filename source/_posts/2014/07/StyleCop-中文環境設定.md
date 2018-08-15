---
title: StyleCop 中文環境設定
tags:
  - StyleCop
date: 2014-07-07 16:51:00
---

Stylecop使用一段時間後，感覺有兩個預設規則不太適合中文環境，所以個人會在專案中取消這兩條規則

首先在專案上按右鍵，選擇StyleCop Settings
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-34eXH7WWiD0/U7pdzXekbgI/AAAAAAAABgs/bnrXu5C4jkk/s1600/01.%E8%A8%AD%E5%AE%9A.png)](http://3.bp.blogspot.com/-34eXH7WWiD0/U7pdzXekbgI/AAAAAAAABgs/bnrXu5C4jkk/s1600/01.%E8%A8%AD%E5%AE%9A.png)</div>
在Rules中的Documentation Rules中，再打開Element Documentation
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-cs3042c1How/U7pdzXgvvJI/AAAAAAAABhI/_83uHNC8X2A/s1600/02.%25E9%25A0%2585%25E7%259B%25AE.png)](http://1.bp.blogspot.com/-cs3042c1How/U7pdzXgvvJI/AAAAAAAABhI/_83uHNC8X2A/s1600/02.%25E9%25A0%2585%25E7%259B%25AE.png)</div>
取消SA1630 DocumentationTextMustContainWhitespace
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-81-MVHrilwI/U7pehwbCa6I/AAAAAAAABhM/CqJfG8KK2nk/s1600/03.SA1630.png)](http://3.bp.blogspot.com/-81-MVHrilwI/U7pehwbCa6I/AAAAAAAABhM/CqJfG8KK2nk/s1600/03.SA1630.png)</div>
取消SA1650 ElementDocumentationMustBeSpelledCorrectly
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-MqmnKPxdPvI/U7peqPbdq_I/AAAAAAAABhU/K6hrfHfMCs0/s1600/04.SA1650.png)](http://1.bp.blogspot.com/-MqmnKPxdPvI/U7peqPbdq_I/AAAAAAAABhU/K6hrfHfMCs0/s1600/04.SA1650.png)</div>
設定好按OK後，專案下面就會多出一個隱藏檔，檔名為Settings.StyleCop
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-FdbCL8bUzX8/U7pe2nDlO-I/AAAAAAAABhc/rvkpRQFm3Ls/s1600/05.%E9%9A%B1%E8%97%8F%E6%AA%94.png)](http://2.bp.blogspot.com/-FdbCL8bUzX8/U7pe2nDlO-I/AAAAAAAABhc/rvkpRQFm3Ls/s1600/05.%E9%9A%B1%E8%97%8F%E6%AA%94.png)</div>
內容是XML格式的文件，可以看的出來，就是把那兩條規則關閉而已
<div><pre class="brush:xml">&lt;StyleCopSettings Version="105"&gt;
    &lt;Analyzers&gt;
        &lt;Analyzer AnalyzerId="StyleCop.CSharp.DocumentationRules"&gt;
            &lt;Rules&gt;
                &lt;Rule Name="DocumentationTextMustContainWhitespace"&gt;
                    &lt;RuleSettings&gt;
                        &lt;BooleanProperty Name="Enabled"&gt;False&lt;/BooleanProperty&gt;
                    &lt;/RuleSettings&gt;
                &lt;/Rule&gt;
                &lt;Rule Name="ElementDocumentationMustBeSpelledCorrectly"&gt;
                    &lt;RuleSettings&gt;
                        &lt;BooleanProperty Name="Enabled"&gt;False&lt;/BooleanProperty&gt;
                    &lt;/RuleSettings&gt;
                &lt;/Rule&gt;
            &lt;/Rules&gt;
            &lt;AnalyzerSettings /&gt;
        &lt;/Analyzer&gt;
    &lt;/Analyzers&gt;
&lt;/StyleCopSettings&gt;
</pre></div>