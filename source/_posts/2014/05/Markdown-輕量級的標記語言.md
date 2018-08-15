---
title: Markdown 輕量級的標記語言
tags: []
date: 2014-05-28 14:40:00
---

Markdown是一種輕量級的標記語言，用來讓人們簡單地編寫**易讀易懂**的純文字檔案，然後轉換成有效的XHTML或HTML格式

Visual Studio中的[Web Essentials](http://vswebessentials.com/features/markdown)擴充套件，已支援Markdown格式的預覽和編輯，只要副檔名為md的文字檔就行了
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-aR6ZJA7wwns/U4VejzBJkyI/AAAAAAAABVU/YgExBpMryjY/s1600/01.+WebEssentials.png)](http://3.bp.blogspot.com/-aR6ZJA7wwns/U4VejzBJkyI/AAAAAAAABVU/YgExBpMryjY/s1600/01.+WebEssentials.png)</div>
# 標題
標題符號：#，1~6數目的#符號對應H1~H6
H1符號：=
H2符號：-
範例：
# H1
## H2
### H3
#### H4
##### H5
###### H6

H1
===

H2
---
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-OPiMGwQ7nlY/U4Ven-1cioI/AAAAAAAABVc/1tVYoEotAng/s1600/02.%E6%A8%99%E9%A1%8C.png)](http://4.bp.blogspot.com/-OPiMGwQ7nlY/U4Ven-1cioI/AAAAAAAABVc/1tVYoEotAng/s1600/02.%E6%A8%99%E9%A1%8C.png)</div>
# 換行 段落
連續兩個空白字元會轉成換行&lt;br /&gt;
連續兩個換行字元會轉成段落&lt;p&gt;&lt;/p&gt;
範例：
第一行 
第二行 
第三行

第二段
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-crIepNApFg4/U4Ver8-veJI/AAAAAAAABVk/FiO1iKNKU9Q/s1600/03.%E6%8F%9B%E8%A1%8C.png)](http://3.bp.blogspot.com/-crIepNApFg4/U4Ver8-veJI/AAAAAAAABVk/FiO1iKNKU9Q/s1600/03.%E6%8F%9B%E8%A1%8C.png)</div>
# 粗體 斜體
斜體符號：一個 * 或 _
粗體符號：兩個 * 或 _
使用方式：將要顯示的文字用符號包圍起來
範例：
*這是斜體文字* 
_這是斜體文字_ 
**這是斜體文字** 
__這是斜體文字__
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-ccv53cpyEGY/U4VevdZMDhI/AAAAAAAABVs/2_JwZhA_l2A/s1600/04.%E7%B2%97%E9%AB%94.png)](http://2.bp.blogspot.com/-ccv53cpyEGY/U4VevdZMDhI/AAAAAAAABVs/2_JwZhA_l2A/s1600/04.%E7%B2%97%E9%AB%94.png)</div>
# 符號列表
符號：* 或 + 或 - 和一個空白
範例：

* 第一行
* 第二行
* 第三行
+ 第四行
+ 第五行
+ 第六行
- 第七行
- 第八行
- 第九行
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-JrNIHFEurJc/U4Veyr4-FvI/AAAAAAAABV0/L4qCBeLZnXQ/s1600/05.%E7%AC%A6%E8%99%9F%E5%88%97%E8%A1%A8.png)](http://1.bp.blogspot.com/-JrNIHFEurJc/U4Veyr4-FvI/AAAAAAAABV0/L4qCBeLZnXQ/s1600/05.%E7%AC%A6%E8%99%9F%E5%88%97%E8%A1%A8.png)</div>
# 數字列表
符號：以數字和.和一個空白作開頭，這裡指定的數字不會是最後呈現的數字
範例：
1\. 第一行
3\. 第二行
5\. 第三行
7\. 第四行
9\. 第五行
1\. 第六行
1\. 第七行
1\. 第八行
1\. 第九行
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-vwYwc7zlNqg/U4Ve1OKPD3I/AAAAAAAABV8/FdT09SUnEO8/s1600/06.%E6%95%B8%E5%AD%97%E5%88%97%E8%A1%A8.png)](http://4.bp.blogspot.com/-vwYwc7zlNqg/U4Ve1OKPD3I/AAAAAAAABV8/FdT09SUnEO8/s1600/06.%E6%95%B8%E5%AD%97%E5%88%97%E8%A1%A8.png)</div>
# 引用
符號：&gt; 和一個空白，可嵌套
範例：

&gt; 引用一句話 
&gt; 第二行 
&gt; 第三行 

&gt; &gt; 嵌套引用 
&gt; &gt; 第二行 
&gt; &gt; 第三行 
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-8rc208iKtEI/U4Ve5BWXl0I/AAAAAAAABWE/ujHf6S5P6QY/s1600/07.%E5%BC%95%E7%94%A8.png)](http://2.bp.blogspot.com/-8rc208iKtEI/U4Ve5BWXl0I/AAAAAAAABWE/ujHf6S5P6QY/s1600/07.%E5%BC%95%E7%94%A8.png)</div>
# 水平分割線&lt;hr /&gt;
符號1：* &nbsp;* &nbsp;*
符號2：- - -
符號3：_ _ _
範例：
第一行
- - -
第二行
* * *
第三行
_ _ _
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-TeCL6swpb30/U4VfJDdvfGI/AAAAAAAABWM/WfmfOeK0iTs/s1600/08.+%E6%B0%B4%E5%B9%B3%E5%88%86%E5%89%B2%E7%B7%9A.png)](http://3.bp.blogspot.com/-TeCL6swpb30/U4VfJDdvfGI/AAAAAAAABWM/WfmfOeK0iTs/s1600/08.+%E6%B0%B4%E5%B9%B3%E5%88%86%E5%89%B2%E7%B7%9A.png)</div>
# 連結
符號：&lt;&gt;
符號：[]

&lt;http://tw.yahoo.com&gt;

[連結的顯示文字](http://tw.yahoo.com "連結的Alt文字")

也可以用定義的方式重覆使用
[Google]

[Google]: http://tw.yahoo.com "Alt"
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-kOtEnbgaJRs/U4VfNvsvWLI/AAAAAAAABWU/X2h1h7HUqng/s1600/08.%E9%80%A3%E7%B5%90.png)](http://4.bp.blogspot.com/-kOtEnbgaJRs/U4VfNvsvWLI/AAAAAAAABWU/X2h1h7HUqng/s1600/08.%E9%80%A3%E7%B5%90.png)</div>

# 圖片
符號：![]
範例：

![找不到圖片的替代文字](http://aaa.jpg "圖片的Alt文字")

也可以用定義的方式重覆使用
![找不到圖片的替代文字][img1]
[img1]: http://bbb.jpg "Alt"
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-sX7ohgPWMtM/U4VfRd_t3cI/AAAAAAAABWc/3QKCg5Uj7Ng/s1600/09.%E5%9C%96%E7%89%87.png)](http://1.bp.blogspot.com/-sX7ohgPWMtM/U4VfRd_t3cI/AAAAAAAABWc/3QKCg5Uj7Ng/s1600/09.%E5%9C%96%E7%89%87.png)</div><div>
</div><div>
</div># 代碼
符號：`，會轉換成&lt;pre&gt;&lt;/pre&gt;
範例：
```cs
public static void Main(string[] args)
{
&nbsp; &nbsp; Console.WriteLine("Hello");
}```

<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-MJtVSYB1jPc/U4VfUm_DmBI/AAAAAAAABWk/1Eomnzx8LSw/s1600/10.Code.png)](http://2.bp.blogspot.com/-MJtVSYB1jPc/U4VfUm_DmBI/AAAAAAAABWk/1Eomnzx8LSw/s1600/10.Code.png)</div>