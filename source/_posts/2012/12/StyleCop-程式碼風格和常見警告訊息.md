---
title: StyleCop 程式碼風格和常見警告訊息
tags:
  - StyleCop
date: 2012-12-24 20:01:00
---

每個檔案的最上面，都加一個檔頭
&nbsp;&nbsp;&nbsp; // &lt;copyright company="CompanyName" file="NameOfFile.cs"&gt;
&nbsp;&nbsp;&nbsp; //&nbsp;&nbsp;&nbsp;&nbsp; Company copyright tag.
&nbsp;&nbsp;&nbsp; // &lt;/copyright&gt;

XML註解
&nbsp;&nbsp;&nbsp; 建構式以Initializes a new instance of the xxx class開頭
&nbsp;&nbsp;&nbsp; 解構式以Finalizes an instance of the xxx class開頭
&nbsp;&nbsp;&nbsp; 屬性以Gets or sets開頭
&nbsp;&nbsp;&nbsp; 註解文字最少兩個字以上，並用空格分隔
&nbsp;&nbsp;&nbsp; 註解文字斷行要用para分隔
&nbsp;&nbsp;&nbsp; 
程式碼撰寫順序
&nbsp;&nbsp;&nbsp; 程式碼撰寫順序: public -&amp;gt; internal -&amp;gt; protected internal -&amp;gt; protected -&amp;gt; private
&nbsp;&nbsp;&nbsp; 程式碼元素撰寫順序: Fields -&amp;gt; Constructor -&amp;gt; Event-&amp;gt; Property -&amp;gt; Method

大小寫規則
&nbsp;&nbsp;&nbsp; Camel Case:私有的內部變數、成員變數、參數
&nbsp;&nbsp;&nbsp; Pascal Case:公開的屬性、方法、事件...
&nbsp;&nbsp;&nbsp; 
其他
&nbsp;&nbsp;&nbsp; using 放到namespace下面
&nbsp;&nbsp;&nbsp; 需使用明確的存取修飾詞
&nbsp;&nbsp;&nbsp; 程式碼中多餘的空白行
&nbsp;&nbsp;&nbsp; 變數不用使用底線

常見錯誤
&nbsp;&nbsp;&nbsp; SA1633 : CSharp.Documentation : The file has no header, the header Xml is invalid, or the header is not located at the top of the file.
&nbsp;&nbsp;&nbsp; 在第一行加入檔頭資訊
&nbsp;&nbsp;&nbsp; 
&nbsp;&nbsp;&nbsp; SA1200 : CSharp.Ordering : All using directives must be placed inside of the namespace.
&nbsp;&nbsp;&nbsp; Using 放到namespace區段下面

&nbsp;&nbsp;&nbsp; SA1027 : CSharp.Spacing : Tabs are not allowed. Use spaces instead.
&nbsp;&nbsp;&nbsp; 工具-&amp;gt;選項-&amp;gt;文字編輯器-&amp;gt;所有語言-&amp;gt;定位點-&amp;gt;插入空格

&nbsp;&nbsp;&nbsp; SA1400 : CSharp.Maintainability : The class must have an access modifier.
&nbsp;&nbsp;&nbsp; 加入明確存取修飾詞

&nbsp;&nbsp;&nbsp; SA1600 : CSharp.Documentation : The class must have a documentation header.
&nbsp;&nbsp;&nbsp; 加入XML Document註解