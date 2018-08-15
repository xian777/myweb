---
title: StyleCop 常見問題與修正方法
tags:
  - StyleCop
date: 2013-01-11 16:55:00
---

## 1\. 單一頁面檢查方法
在空白地方按右鍵，選擇Run StyleCop，就只會檢查目前頁面

<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-0l67G3vlzQ4/UO_I6oV3ySI/AAAAAAAAAqA/UEK5h8PGDpc/s1600/00.RunStyleCop.png)](http://3.bp.blogspot.com/-0l67G3vlzQ4/UO_I6oV3ySI/AAAAAAAAAqA/UEK5h8PGDpc/s1600/00.RunStyleCop.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>

## 2\. 沒有檔頭宣告

### 錯誤訊息
The file has no header, the header Xml is invalid, or the header is not located at the top of the file.

### 修正方法
程式碼第一行加上檔頭宣告，格式如下
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Cpp1sApPGuQ/UO_PTzM4scI/AAAAAAAAArg/aAWRAQ6UqiI/s1600/07.Header.png)](http://2.bp.blogspot.com/-Cpp1sApPGuQ/UO_PTzM4scI/AAAAAAAAArg/aAWRAQ6UqiI/s1600/07.Header.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>如果是自動產生的檔案，可用auto-generated標籤略過
// &lt;auto-generated /&gt;

<div class="separator" style="clear: both; text-align: left;"></div>

## 3\. 縮排格式不正確
錯誤訊息
Tabs are not allowed. Use spaces instead. 

### 修正方法
工具--&gt;選項--&gt;文字編輯器--&gt;所有語言--&gt;定位點
定位點和縮排大小都設定成4，並選擇插入空格的方式
開啟原始碼，使用CTRL+k, d重整程式碼即可
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-9S6GXTgtBsM/UO_JHDLoHOI/AAAAAAAAAqI/ln0-f0prpcE/s1600/01.tab.png)](http://2.bp.blogspot.com/-9S6GXTgtBsM/UO_JHDLoHOI/AAAAAAAAAqI/ln0-f0prpcE/s1600/01.tab.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>

## 4\. Using指示詞位置
錯誤訊息
All using directives must be placed inside of the namespace.

### 修正方法
把所有using指示詞剪下，放到namespace下面
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-bCvpbNrMUgs/UO_OgWrg87I/AAAAAAAAArU/FLhlVA8UfbA/s1600/06.using.png)](http://4.bp.blogspot.com/-bCvpbNrMUgs/UO_OgWrg87I/AAAAAAAAArU/FLhlVA8UfbA/s1600/06.using.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>

## 5\. Using 指示詞順序

### 錯誤訊息
Using directives must be sorted alphabetically by the namespaces.

### 修正方法
命名空間按照字母排序
系統內建的命名空間先排，再排自訂的命名空間

## 6\. 明確指定修飾詞
錯誤訊息
The class must have an access modifier.

### 修正方法
加上明確的修飾詞，public、private、protected、internal、protected internal
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-vG6tSwtR4zM/UO_Pd8mz57I/AAAAAAAAAro/gDoCLYX826Y/s1600/08.Modify.png)](http://4.bp.blogspot.com/-vG6tSwtR4zM/UO_Pd8mz57I/AAAAAAAAAro/gDoCLYX826Y/s1600/08.Modify.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>

## 7\. 沒有文件註解

### 錯誤訊息
The class must have a documentation header.
The method must have a documentation header.
The property must have a documentation header.

### 修正方法
加上XML文件註解
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-AsbybJiDFKo/UO_PjIJgd_I/AAAAAAAAArw/3wSBqeQq1Kw/s1600/09.Comment.png)](http://1.bp.blogspot.com/-AsbybJiDFKo/UO_PjIJgd_I/AAAAAAAAArw/3wSBqeQq1Kw/s1600/09.Comment.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>

## 8\. 中文註解問題

### 錯誤訊息
The documentation text within the summary tag contains incorrectly spelled words: 中文字 &nbsp; 

### 修正方法
在專案上按右鍵，選擇StyleCop Settings
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-d8tv6rESvGw/UO_JN4dMbaI/AAAAAAAAAqQ/y-pLFVYwL2Y/s1600/02.Setting.png)](http://1.bp.blogspot.com/-d8tv6rESvGw/UO_JN4dMbaI/AAAAAAAAAqQ/y-pLFVYwL2Y/s1600/02.Setting.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>在Options上，預設Culture是en-US，隨便選擇其他的語系後按確定
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-fc-JQlB0g6E/UO_JQT7A2YI/AAAAAAAAAqY/B-jxs-_870Q/s1600/03.Option.png)](http://3.bp.blogspot.com/-fc-JQlB0g6E/UO_JQT7A2YI/AAAAAAAAAqY/B-jxs-_870Q/s1600/03.Option.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>在方案總管上按顯示所有檔案，會看到產生出Settings.StyleCop的檔案
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-CPE1oznMNvI/UO_JTFTdRkI/AAAAAAAAAqg/fBOsEO7X4KM/s1600/04.SolutionExplorer.png)](http://2.bp.blogspot.com/-CPE1oznMNvI/UO_JTFTdRkI/AAAAAAAAAqg/fBOsEO7X4KM/s1600/04.SolutionExplorer.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>打開後把Culture修改成zh-TW就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-aN0pltuovsA/UO_JVUTotOI/AAAAAAAAAqo/We5R_b-0Md0/s1600/05.Culture.png)](http://3.bp.blogspot.com/-aN0pltuovsA/UO_JVUTotOI/AAAAAAAAAqo/We5R_b-0Md0/s1600/05.Culture.png)</div>
<div class="separator" style="clear: both; text-align: left;"></div>

## 9\. 文件註解內容中沒有空格

### 錯誤訊息
The documentation text within the summary tag does not contain any whitespace between words, indicating that it most likely does not follow a proper grammatical structure required for documentation text.

### 修正方法
注解文字中加入空格

## 10\. 一般屬性註解格式

### 錯誤訊息
The property's documentation summary text must begin with: Gets or sets

### 修正方法
註解文字開頭使用 Gets or sets
<pre class="brush:csharp">/// &lt;summary&gt;
/// Gets or sets MyPropData
/// &lt;/summary&gt;
public int MyPropData { get; set; }
</pre>

## 11\. 布林屬性註解格式

### 錯誤訊息
The property's documentation summary text must begin with: Gets or sets a value indicating whether

### 修正方法
註解文字開頭使用 Gets or sets a value indicating whether
<pre class="brush:xml">/// &lt;summary&gt;
/// Gets or sets a value indicating whether MyBooleanData
/// &lt;/summary&gt;
public bool MyBooleanData { get; set; }
</pre>

## 12\. 建構式註解格式

### 錯誤訊息
The documentation text within the constructor's summary tag must begin with the text: Initializes a new instance of the &lt;see cref="類別名稱" /&gt; class.

### 修正方法
註解文字開頭使用Initializes a new instance of the &lt;see cref="類別名稱" /&gt; class.

<pre class="brush:xml">/// &lt;summary&gt;
/// Initializes a new instance of the &lt;see cref="Program" /&gt; class.
/// &lt;/summary&gt;
public Program()
{
}
</pre>

## 13\. 程式碼元素順序

### 錯誤訊息
All methods must be placed after all properties.
All private properties must be placed after all public properties.

### 修正方法
程式碼撰寫順序: public -&gt; internal -&gt; protected internal -&gt; protected -&gt; private
程式碼元素撰寫順序: Fields -&gt; Constructor -&gt; Event-&gt; Property -&gt; Method

## 14\. 函數多行參數格式

### 錯誤訊息
If the method parameters are on separate lines, the first parameter must begin on the line beneath the name of the method. &nbsp; 

### 修正方法
每個參數獨立一行
<pre class="brush:xml">Console.WriteLine(
    "arg1:{0}, arg2:{1}, arg3:{2}",
    args[0], 
    args[1], 
    args[2]);
</pre>

## 15\. 呼叫同類別的成員需加入this.前綴詞

### 錯誤訊息
The call to MyData must begin with the 'this.' prefix to indicate that the item is a member of the class.

### 修正方法
明確使用this前綴詞來呼叫同類別的屬性、方法
<pre class="brush:xml">/// &lt;summary&gt;
/// Initializes a new instance of the &lt;see cref="Program" /&gt; class.
/// &lt;/summary&gt;
public Program()
{
    this.MyPropData = 123;
}

/// &lt;summary&gt;
/// Gets or sets MyPropData
/// &lt;/summary&gt;
public int MyPropData { get; set; }
</pre>