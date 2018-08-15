---
title: ADFS 2.0 新增信任的信賴憑證者
tags:
  - ADFS
  - Claims Base
  - SSO
date: 2014-02-14 14:44:00
---

接下來開始新增RP(Relying Party)
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-vLPrmmAQ0U8/Uv2JXZQ1VfI/AAAAAAAABC8/eeIGdQSZH4M/s1600/01.png)](http://2.bp.blogspot.com/-vLPrmmAQ0U8/Uv2JXZQ1VfI/AAAAAAAABC8/eeIGdQSZH4M/s1600/01.png)</div>
設定精靈的畫面
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-Mua3r26Sssg/Uv2JXWvLLVI/AAAAAAAABDI/2ge-kfXg504/s1600/02.png)](http://2.bp.blogspot.com/-Mua3r26Sssg/Uv2JXWvLLVI/AAAAAAAABDI/2ge-kfXg504/s1600/02.png)</div>
這裡用手動輸入為例子
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-b3dHsdW6Lgc/Uv2JYmulxHI/AAAAAAAABDw/nlRPavaRvww/s1600/03.png)](http://3.bp.blogspot.com/-b3dHsdW6Lgc/Uv2JYmulxHI/AAAAAAAABDw/nlRPavaRvww/s1600/03.png)</div>
輸入一個給人用來識別的名稱
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-ZjIYsxbZCrQ/Uv2JYNqfZgI/AAAAAAAABDM/MfI-6QVNz2Y/s1600/04.png)](http://3.bp.blogspot.com/-ZjIYsxbZCrQ/Uv2JYNqfZgI/AAAAAAAABDM/MfI-6QVNz2Y/s1600/04.png)</div>
選擇AD FS 2.0 設定檔
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-9ilWycLTR5E/Uv2JYdrP3NI/AAAAAAAABDY/OOm8gKBttTs/s1600/05.png)](http://1.bp.blogspot.com/-9ilWycLTR5E/Uv2JYdrP3NI/AAAAAAAABDY/OOm8gKBttTs/s1600/05.png)</div>
這裡用簡單的例子不加密所以直接下一步
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-EHbTfRL4WUk/Uv2JYx32YjI/AAAAAAAABDg/iMoh1N6aRxI/s1600/06.png)](http://1.bp.blogspot.com/-EHbTfRL4WUk/Uv2JYx32YjI/AAAAAAAABDg/iMoh1N6aRxI/s1600/06.png)</div>
啟用 WS-Federation 被動通訊協定的支援，注意SSL和結尾的/
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-zgPv-ndCWn8/Uv2KjlZzWRI/AAAAAAAABE4/qKrCLGZ-uHo/s1600/07.png)](http://2.bp.blogspot.com/-zgPv-ndCWn8/Uv2KjlZzWRI/AAAAAAAABE4/qKrCLGZ-uHo/s1600/07.png)</div>
這裡的識別碼是程式要看的，也就是audienceUris
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-KVQ9oz9PfYM/Uv2JaIn9wnI/AAAAAAAABEQ/M04yyBNT8bU/s1600/08.png)](http://2.bp.blogspot.com/-KVQ9oz9PfYM/Uv2JaIn9wnI/AAAAAAAABEQ/M04yyBNT8bU/s1600/08.png)</div>
允許所有使用者存取
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-lqmg6yTu6YA/Uv2JaPAqK1I/AAAAAAAABD0/xP9qJb5EQfc/s1600/09.png)](http://3.bp.blogspot.com/-lqmg6yTu6YA/Uv2JaPAqK1I/AAAAAAAABD0/xP9qJb5EQfc/s1600/09.png)</div>
準備新增信任
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-9gtrMYiSYlY/Uv2Jaq2uxWI/AAAAAAAABD4/xppCp5yhdXk/s1600/10.png)](http://1.bp.blogspot.com/-9gtrMYiSYlY/Uv2Jaq2uxWI/AAAAAAAABD4/xppCp5yhdXk/s1600/10.png)</div>
新增完成，接下來順便新增要轉換的資料
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-FUHvQGzfAuI/Uv2Ja7_86YI/AAAAAAAABEM/gs0YHRPEfaE/s1600/11.png)](http://1.bp.blogspot.com/-FUHvQGzfAuI/Uv2Ja7_86YI/AAAAAAAABEM/gs0YHRPEfaE/s1600/11.png)</div>
<div class="separator" style="clear: both; text-align: center;"></div>發佈轉換規則中新增規則
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-K-Dv1xXNaoE/Uv2MIkLNe7I/AAAAAAAABFM/kOth2Ps7GgE/s1600/12.png)](http://1.bp.blogspot.com/-K-Dv1xXNaoE/Uv2MIkLNe7I/AAAAAAAABFM/kOth2Ps7GgE/s1600/12.png)</div>
這裡以LDAP屬性為例
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-Q39atvMpEj4/Uv2JcK2Jq2I/AAAAAAAABEc/DIpVLn9xyIE/s1600/13.png)](http://1.bp.blogspot.com/-Q39atvMpEj4/Uv2JcK2Jq2I/AAAAAAAABEc/DIpVLn9xyIE/s1600/13.png)</div>
把LDAP的屬性，轉成要傳出的宣告類型
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-UwzwR31Cm84/Uv26uGcbNCI/AAAAAAAABFo/jEdouWyYxHE/s1600/14.png)](http://3.bp.blogspot.com/-UwzwR31Cm84/Uv26uGcbNCI/AAAAAAAABFo/jEdouWyYxHE/s1600/14.png)</div>
轉換規則設定完成
<div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;"></div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-M6SbsGmKqCA/Uv27ST1MLuI/AAAAAAAABFw/OV4YcWFN93w/s1600/15.png)](http://1.bp.blogspot.com/-M6SbsGmKqCA/Uv27ST1MLuI/AAAAAAAABFw/OV4YcWFN93w/s1600/15.png)</div>
到此新增RP完成
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-eyjii0WijiE/Uv2JdDP53FI/AAAAAAAABEw/6KEtX5HuIvo/s1600/16.png)](http://2.bp.blogspot.com/-eyjii0WijiE/Uv2JdDP53FI/AAAAAAAABEw/6KEtX5HuIvo/s1600/16.png)</div>