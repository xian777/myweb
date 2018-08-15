---
title: TeamCity 改用網域帳號LDAP登入
tags:
  - LDAP
  - TeamCity
date: 2012-11-29 22:07:00
---

## 如果開發環境中有網域管理的話，可以把登入模式改LDAP模組登入
打開C:\ProgramData\JetBrains\TeamCity\config\main-config.xml
![](http://1.bp.blogspot.com/-LkzYbvwCZuw/ULdqGx9BwaI/AAAAAAAAAfQ/6CW0ZAsBGI8/s1600/01.MainConfig.png)](http://1.bp.blogspot.com/-LkzYbvwCZuw/ULdqGx9BwaI/AAAAAAAAAfQ/6CW0ZAsBGI8/s1600/01.MainConfig.png)

## 裡面的auth-type節點中，預設會是DefaultLoginModule
```xml
<login-module class="jetbrains.buildServer.serverSide.impl.auth.DefaultLoginModule" />
```

## 將模組改成LDAPLoginModule就行了
```xml
<login-module class="jetbrains.buildServer.serverSide.impl.auth.LDAPLoginModule" />
```

## 再來是設定LDAP的環境參數，在config資料夾中，有一個ldap-config.properties.dist的範本檔
![](http://4.bp.blogspot.com/-WMSkZa1XkIk/ULdojCaepFI/AAAAAAAAAfI/vMVyOCm631c/s1600/ldapConfig.png)](http://4.bp.blogspot.com/-WMSkZa1XkIk/ULdojCaepFI/AAAAAAAAAfI/vMVyOCm631c/s1600/ldapConfig.png)

## 複制成ldap-config.properties這個檔案，再用文字編輯器打開來修改，主要有以下幾個項目
## 把example換成自已的網域名稱 
```xml
#設定AD的位置
java.naming.provider.url=ldap://dc.example.com:389/DC=example,DC=com
 
#設定登入的時後，帳號格式不用包含\或是@
teamcity.auth.loginFilter=[^/\\\\@]+
 
#配合上一個設定，和AD驗證的時後，送過去的帳號，前面自動補上網域名稱
teamcity.auth.formatDN=example\\$login$
```

* 設定這三個項目，其他改用預設值，就可以用網域驗證了
* 登入後如果要同步帳號資料，可以再多加以下幾個選項
```xml
java.naming.security.principal=<username>
java.naming.security.credentials=<password>
teamcity.users.username=sAMAccountName
teamcity.options.users.synchronize=true
teamcity.users.filter=(objectClass=user)
teamcity.users.property.displayName=displayName
teamcity.users.property.email=mail
```

## 第一次登入的時後，會需要設定帳號成管理員
![](http://4.bp.blogspot.com/-YeLe1Eu1ow8/ULdoiVM37FI/AAAAAAAAAfA/wpXiVMbloMI/s1600/01.LDAP.png)](http://4.bp.blogspot.com/-YeLe1Eu1ow8/ULdoiVM37FI/AAAAAAAAAfA/wpXiVMbloMI/s1600/01.LDAP.png)

## 如果有問題，可以查一下log
![](http://4.bp.blogspot.com/-msOoL42fhGg/ULdri4HdINI/AAAAAAAAAfY/njs3tVOcjv8/s1600/02.log.png)](http://4.bp.blogspot.com/-msOoL42fhGg/ULdri4HdINI/AAAAAAAAAfY/njs3tVOcjv8/s1600/02.log.png)

## 參考資料
* [Typical LDAP Configurations](http://confluence.jetbrains.net/display/TCD7/Typical+LDAP+Configurations)
* [LDAP Integration](http://confluence.jetbrains.net/display/TCD7/LDAP+Integration#LDAPIntegration-ActiveDirectory)
* [How To Set Up Secure LDAP Authentication with TeamCity](http://therightstuff.de/CommentView,guid,2e19b03d-6ee1-49c1-b8c9-da5f3db7826f.aspx)