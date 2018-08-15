---
title: 手動設定WIF
tags:
  - Claims Base
date: 2014-03-24 11:11:00
---

<div>首先引用System.IdentityModel和System.IdentityModel.Service這兩個元件</div><div class="separator" style="clear: both; text-align: center;">[![](http://1.bp.blogspot.com/-JeEQBHGiBCA/Uy-gIfqaWrI/AAAAAAAABHg/CKFEhn8Di6I/s1600/01.add+component.png)](http://1.bp.blogspot.com/-JeEQBHGiBCA/Uy-gIfqaWrI/AAAAAAAABHg/CKFEhn8Di6I/s1600/01.add+component.png)</div>

再來到web.config加入幾個設定
先加入這兩個元件的configSection
<div><pre class="brush:xml">&lt;configSections&gt;
    &lt;section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" /&gt;
    &lt;section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" /&gt;
&lt;/configSections&gt;
</pre></div>
再來在System.Web區段中，把網站的驗證模組設定None和不允許匿名登入
<div><pre class="brush:xml">&lt;system.web&gt;
    &lt;authentication mode="None" /&gt;
    &lt;authorization&gt;
        &lt;deny users="?" /&gt;
    &lt;/authorization&gt;
    &lt;compilation debug="true" targetFramework="4.5"/&gt;
    &lt;httpRuntime targetFramework="4.5"/&gt;
&lt;/system.web&gt;
</pre></div>
再來在System.webServer區段中，啟用兩個HttpModule
<div><pre class="brush:xml">&lt;system.webServer&gt;
    &lt;modules&gt;
        &lt;add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" /&gt;
        &lt;add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" /&gt;
    &lt;/modules&gt;
&lt;/system.webServer&gt;
</pre></div>
最後加入WIF的設定
<div><pre class="brush:xml">&lt;system.identityModel&gt;
    &lt;identityConfiguration&gt;
        &lt;audienceUris&gt;
            &lt;add value="http://localhost:12345/" /&gt;
        &lt;/audienceUris&gt;
        &lt;securityTokenHandlers&gt;
            &lt;add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /&gt;
            &lt;remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" /&gt;
        &lt;/securityTokenHandlers&gt;
        &lt;certificateValidation certificateValidationMode="None" /&gt;
        &lt;issuerNameRegistry type="System.IdentityModel.Tokens.ValidatingIssuerNameRegistry, System.IdentityModel.Tokens.ValidatingIssuerNameRegistry"&gt;
            &lt;authority name="MySTS"&gt;
                &lt;keys&gt;
                    &lt;add thumbprint="簽署憑證的姆指紋" /&gt;
                &lt;/keys&gt;
                &lt;validIssuers&gt;
                    &lt;add name="MySTS" /&gt;
                &lt;/validIssuers&gt;
            &lt;/authority&gt;
        &lt;/issuerNameRegistry&gt;
    &lt;/identityConfiguration&gt;
&lt;/system.identityModel&gt;
&lt;system.identityModel.services&gt;
    &lt;federationConfiguration&gt;
        &lt;cookieHandler requireSsl="false" /&gt;
        &lt;wsFederation passiveRedirectEnabled="true"
                        issuer="http://sts.developer.idv.tw/"
                        realm="http://localhost:51337/"
                        requireHttps="false" /&gt;
    &lt;/federationConfiguration&gt;
&lt;/system.identityModel.services&gt;
</pre></div>
在這裡有個設定，需要加入一個NuGet參考
System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
<div class="separator" style="clear: both; text-align: center;">[![](http://4.bp.blogspot.com/-5jv6U3EKwtU/Uy-iKggj3KI/AAAAAAAABHs/nGIR9YSbP5k/s1600/02.package.png)](http://4.bp.blogspot.com/-5jv6U3EKwtU/Uy-iKggj3KI/AAAAAAAABHs/nGIR9YSbP5k/s1600/02.package.png)</div>