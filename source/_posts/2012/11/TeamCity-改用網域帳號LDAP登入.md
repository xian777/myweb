---
title: TeamCity 改用網域帳號LDAP登入
tags:
  - LDAP
  - TeamCity
date: 2012-11-29 22:07:00
---

<div class="separator" style="clear: both; text-align: left;">如果開發環境中有網域管理的話，可以把登入模式改LDAP模組登入</div>
<div class="separator" style="clear: both; text-align: left;">打開C:\ProgramData\JetBrains\TeamCity\config\main-config.xml</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-LkzYbvwCZuw/ULdqGx9BwaI/AAAAAAAAAfQ/6CW0ZAsBGI8/s1600/01.MainConfig.png)](http://1.bp.blogspot.com/-LkzYbvwCZuw/ULdqGx9BwaI/AAAAAAAAAfQ/6CW0ZAsBGI8/s1600/01.MainConfig.png)</div><div class="separator" style="clear: both; text-align: left;">
</div>裡面的auth-type節點中，預設會是DefaultLoginModule

<div class="separator" style="clear: both; text-align: left;"></div><pre class="brush: xml">&lt;login-module class="jetbrains.buildServer.serverSide.impl.auth.DefaultLoginModule" /&gt;
</pre>
<div class="separator" style="clear: both; text-align: left;">將模組改成LDAPLoginModule就行了</div>
<pre class="brush: xml">&lt;login-module class="jetbrains.buildServer.serverSide.impl.auth.LDAPLoginModule" /&gt;
</pre>
<div class="separator" style="clear: both; text-align: left;">再來是設定LDAP的環境參數，在config資料夾中，有一個ldap-config.properties.dist的範本檔</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-WMSkZa1XkIk/ULdojCaepFI/AAAAAAAAAfI/vMVyOCm631c/s1600/ldapConfig.png)](http://4.bp.blogspot.com/-WMSkZa1XkIk/ULdojCaepFI/AAAAAAAAAfI/vMVyOCm631c/s1600/ldapConfig.png)</div><div class="separator" style="clear: both; text-align: left;">
</div>複制成ldap-config.properties這個檔案，再用文字編輯器打開來修改，主要有以下幾個項目
把example換成自已的網域名稱 

<div class="separator" style="clear: both; text-align: left;"></div><pre class="brush: perl">#設定AD的位置
java.naming.provider.url=ldap://dc.example.com:389/DC=example,DC=com

#設定登入的時後，帳號格式不用包含\或是@
teamcity.auth.loginFilter=[^/\\\\@]+

#配合上一個設定，和AD驗證的時後，送過去的帳號，前面自動補上網域名稱
teamcity.auth.formatDN=example\\$login$
</pre>
<div class="separator" style="clear: both; text-align: left;">設定這三個項目，其他改用預設值，就可以用網域驗證了</div><div class="separator" style="clear: both; text-align: left;">登入後如果要同步帳號資料，可以再多加以下幾個選項</div><div><pre class="brush: perl">java.naming.security.principal=&lt;username&gt;
java.naming.security.credentials=&lt;password&gt;
teamcity.users.username=sAMAccountName
teamcity.options.users.synchronize=true
teamcity.users.filter=(objectClass=user)
teamcity.users.property.displayName=displayName
teamcity.users.property.email=mail
</pre></div>
<div class="separator" style="clear: both; text-align: left;">第一次登入的時後，會需要設定帳號成管理員</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-YeLe1Eu1ow8/ULdoiVM37FI/AAAAAAAAAfA/wpXiVMbloMI/s1600/01.LDAP.png)](http://4.bp.blogspot.com/-YeLe1Eu1ow8/ULdoiVM37FI/AAAAAAAAAfA/wpXiVMbloMI/s1600/01.LDAP.png)</div>
<div class="separator" style="clear: both; text-align: left;">如果有問題，可以查一下log</div><div class="separator" style="clear: both; text-align: left;">log位置在 C:\TeamCity\logs</div><div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-msOoL42fhGg/ULdri4HdINI/AAAAAAAAAfY/njs3tVOcjv8/s1600/02.log.png)](http://4.bp.blogspot.com/-msOoL42fhGg/ULdri4HdINI/AAAAAAAAAfY/njs3tVOcjv8/s1600/02.log.png)</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">
</div><div class="separator" style="clear: both; text-align: left;">參考資料</div>
<div class="separator" style="clear: both; text-align: left;">[Typical LDAP Configurations](http://confluence.jetbrains.net/display/TCD7/Typical+LDAP+Configurations)</div>
<div class="separator" style="clear: both; text-align: left;">[LDAP Integration](http://confluence.jetbrains.net/display/TCD7/LDAP+Integration#LDAPIntegration-ActiveDirectory)</div>
<div class="separator" style="clear: both; text-align: left;">[How To Set Up Secure LDAP Authentication with TeamCity](http://therightstuff.de/CommentView,guid,2e19b03d-6ee1-49c1-b8c9-da5f3db7826f.aspx)</div>
上一篇:[TeamCity 建置後打包和發佈套件](http://blog.developer.idv.tw/2012/11/teamcity_6277.html)
下一篇:[TeamCity 安裝BuildAgent](http://blog.developer.idv.tw/2012/11/teamcity-buildagent.html)