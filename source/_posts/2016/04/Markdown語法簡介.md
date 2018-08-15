---
title: Markdown語法簡介
tags: []
date: 2016-04-26 10:24:00
---

# Markdown語法簡介

## 標題

    <span class="hljs-header"># H1</span>
    <span class="hljs-header">## H2</span>
    <span class="hljs-header">### H3</span>
    <span class="hljs-header">#### H4</span>
    <span class="hljs-header">##### H5</span>
    <span class="hljs-header">###### H6</span>`</pre>

    ## 換行與段落

*   一個換行字元會轉成換行`&lt;br /&gt;`
*   兩個換行字元會轉成段落`&lt;p&gt;&lt;/p&gt;`<pre class="prettyprint">`第一段
    第一行
    第二行

    第二段
    第一行
    第二行`</pre>

    ## 字體
    <pre class="prettyprint">`<span class="hljs-emphasis">*斜體*</span>
    <span class="hljs-strong">**粗體**</span>
    <span class="hljs-strong">***粗斜體**</span>*
    ~~刪除線~~`</pre>

    ## 引言
    <pre class="prettyprint">`<span class="hljs-blockquote">&gt; 用&gt;和一個空白表示</span>
    &gt;&gt; 多個&gt;表示嵌套`</pre>

    ## 水平分隔線
    <pre class="prettyprint">`三個以上的星號、連字號、底線表示
    不能有空白或其他的文字
    <span class="hljs-header">***
    ---</span>
    <span class="hljs-emphasis">___</span>`</pre>

    ## 無序清單
    <pre class="prettyprint">`<span class="hljs-bullet">* </span>星號加空白
    <span class="hljs-code">    * 加Tab可嵌套清單</span>
    <span class="hljs-bullet">+ </span>加號也可以
    <span class="hljs-bullet">- </span>減號也可以`</pre>

    ## 有序清單
    <pre class="prettyprint">`<span class="hljs-bullet">1\. </span>格式為一個數字加小數點加空白
    <span class="hljs-bullet">2\. </span>數字本身順序不重要會自動遞增
    <span class="hljs-code">    1\. 一樣用加Tab可以嵌套</span>`</pre>

    ## 超連結
    <pre class="prettyprint">`<span class="hljs-bullet">* </span>[<span class="hljs-link_label">行內連結</span>](<span class="hljs-link_url">https://www.google.com</span>)
    <span class="hljs-bullet">* </span>[<span class="hljs-link_label">帶標題的行內連結</span>](<span class="hljs-link_url">https://www.google.com "Google WebSite"</span>)
    <span class="hljs-bullet">* </span>[<span class="hljs-link_label">參考連結</span>][<span class="hljs-link_reference">Google Link</span>]
    [<span class="hljs-link_reference">Google Link</span>]:<span class="hljs-link_url"> https://www.google.com</span>`</pre>

    ## 圖片
    <pre class="prettyprint">`行內格式：
    ![<span class="hljs-link_label">圖片文字</span>](<span class="hljs-link_url">01.png "圖片Alt"</span>)

    參考連結格式：
    ![<span class="hljs-link_label">圖片文字</span>][<span class="hljs-link_reference">logo</span>]
    [<span class="hljs-link_reference">logo</span>]:<span class="hljs-link_url"> 01.png "圖片Alt"</span>`</pre>

    ## 程式代碼與語法高亮

*   單行代碼用一個`前後包起來
*   多行代碼用三個`前後包起來
*   語法高亮在`符號後加入語法的名稱<pre>`

    `</pre><pre class="prettyprint">`Console<span class="hljs-preprocessor">.WriteLine</span>(<span class="hljs-string">"Hello"</span>)<span class="hljs-comment">;</span>`</pre>

    ## 表格
    <pre class="prettyprint">`冒號用來對齊的
    預設為靠左對齊
    放在右邊就是靠右對齊
    左右都放就是靠中對齊

    | 欄位一        | 欄位二           |  欄位三 |
    | ------------- |-------------:| :-----:|
    | col 3 is      | right-aligned | $1600 |
    | col 2 is      | centered      |   $12 |
    | zebra stripes | are neat      |    $1 |

    表示中要跳脫表格用到的符號，需要用html編碼的方式表示
    空白是&amp;nbsp;
    |是&amp;#124;