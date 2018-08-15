---
title: ADFS 2.0 使用VS2013設定Claims-Aware Application
tags:
  - ADFS
  - Claims Base
  - SSO
date: 2014-02-14 15:19:00
---

首先新增一個Web專案
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-frB8XFpPq-M/Uv2_nlHATGI/AAAAAAAABGE/7bdvPVOlIGM/s1600/01.png)](http://4.bp.blogspot.com/-frB8XFpPq-M/Uv2_nlHATGI/AAAAAAAABGE/7bdvPVOlIGM/s1600/01.png)</div>
這裡以MVC專案為例，選擇變更驗證
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-EQ_0_80Szks/Uv2_nuTN4XI/AAAAAAAABGU/KMEiOWyKHHs/s1600/02.png)](http://1.bp.blogspot.com/-EQ_0_80Szks/Uv2_nuTN4XI/AAAAAAAABGU/KMEiOWyKHHs/s1600/02.png)</div>
驗證方式改成組織帳戶，登入方式改成內部部署，並輸入FederationMetadata.xml的網址和應用程式的網址，需要SSL
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-WUWRhLcsXsk/Uv2_oQgw0kI/AAAAAAAABHQ/H9QJB3QEHA0/s1600/03.png)](http://2.bp.blogspot.com/-WUWRhLcsXsk/Uv2_oQgw0kI/AAAAAAAABHQ/H9QJB3QEHA0/s1600/03.png)</div>
FederationMetadata.xml的位置可在ADFS的服務&gt;&gt;端點找到
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-bDrc3om0kn8/Uv2_n9UMtUI/AAAAAAAABGM/VL4uWs_8kEw/s1600/03-1.png)](http://1.bp.blogspot.com/-bDrc3om0kn8/Uv2_n9UMtUI/AAAAAAAABGM/VL4uWs_8kEw/s1600/03-1.png)</div>
驗證方式變更為組織驗證(內部部署)後，按下確定建立新專案
<div class="separator" style="clear: both; text-align: center;">[![](http://2.bp.blogspot.com/-erHnn5RET2c/Uv2_oYDieJI/AAAAAAAABGc/01T-6PJBLqw/s1600/04.png)](http://2.bp.blogspot.com/-erHnn5RET2c/Uv2_oYDieJI/AAAAAAAABGc/01T-6PJBLqw/s1600/04.png)</div>
將網站部署到IIS後，輸入該網站的網址來測試一下，因為SSL用的憑證是自已發的，所以會有警告訊息
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-zYDsYTeus3I/Uv2_ozmIA3I/AAAAAAAABGk/gDEDCuTTjHo/s1600/05.png)](http://3.bp.blogspot.com/-zYDsYTeus3I/Uv2_ozmIA3I/AAAAAAAABGk/gDEDCuTTjHo/s1600/05.png)</div>
接下來會轉向到STS去做驗證，一樣會有SSL的警告訊息
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-SVRzTLtiLdo/Uv2_pLZkSnI/AAAAAAAABGs/zJuMX9PP9qE/s1600/06.png)](http://4.bp.blogspot.com/-SVRzTLtiLdo/Uv2_pLZkSnI/AAAAAAAABGs/zJuMX9PP9qE/s1600/06.png)</div>
接下來預設是會跳出視窗讓你輸入帳密
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-b9N82h1FKKw/Uv2_pfF1y0I/AAAAAAAABG0/V_Df7_i5o90/s1600/07.png)](http://3.bp.blogspot.com/-b9N82h1FKKw/Uv2_pfF1y0I/AAAAAAAABG0/V_Df7_i5o90/s1600/07.png)</div>
如果要改成登入頁面的方式，可以到adfs的web.config中去設定一下
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-pokmnOGYPjo/Uv2_qC7sxYI/AAAAAAAABHI/NDSCVtUDzKs/s1600/09.png)](http://4.bp.blogspot.com/-pokmnOGYPjo/Uv2_qC7sxYI/AAAAAAAABHI/NDSCVtUDzKs/s1600/09.png)</div>
找到localAuthenticationTypes區段，把forms的順序換到最上面即可
如果要自訂登入頁面，就把後面的Page指定的頁面換掉即可
<div><pre class="brush:xml">&lt;microsoft.identityServer.web&gt;
    &lt;localAuthenticationTypes&gt;
        &lt;!-- 把Forms換到最上面 後面的page就是登入頁面--&gt;
        &lt;add name="Forms" page="FormsSignIn.aspx" /&gt;
        &lt;add name="Integrated" page="auth/integrated/" /&gt;
        &lt;add name="TlsClient" page="auth/sslclient/" /&gt;
        &lt;add name="Basic" page="auth/basic/" /&gt;
    &lt;/localAuthenticationTypes&gt;
    &lt;commonDomainCookie writer="" reader="" /&gt;
    &lt;context hidden="true" /&gt;
    &lt;error page="Error.aspx" /&gt;
    &lt;acceptedFederationProtocols saml="true" wsFederation="true" /&gt;
    &lt;homeRealmDiscovery page="HomeRealmDiscovery.aspx" /&gt;
    &lt;persistIdentityProviderInformation enabled="true" lifetimeInDays="30" /&gt;
    &lt;singleSignOn enabled="true" /&gt;
&lt;/microsoft.identityServer.web&gt;
&lt;/configuration&gt;
</pre></div>
登入的方式就會變成一般的登入頁面
<div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-3Zv2nGLO5XU/Uv2_qZlBQEI/AAAAAAAABHM/AAx2rkWN9PQ/s1600/10.png)](http://1.bp.blogspot.com/-3Zv2nGLO5XU/Uv2_qZlBQEI/AAAAAAAABHM/AAx2rkWN9PQ/s1600/10.png)</div>
帳號驗證成功後就會回到一開始的網站，並顯示出轉送規則中的名稱
<div class="separator" style="clear: both; text-align: center;">[![](http://3.bp.blogspot.com/-R05voaQHWho/Uv2_qDzS_oI/AAAAAAAABHA/vTwZ5O4h9Ls/s1600/08.png)](http://3.bp.blogspot.com/-R05voaQHWho/Uv2_qDzS_oI/AAAAAAAABHA/vTwZ5O4h9Ls/s1600/08.png)</div>