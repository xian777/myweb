---
title: HTTP Status Code
tags:
  - HTTP
date: 2013-08-16 15:54:00
---

# HTTP Status Code 

## 100~199 訊息狀態碼
<div><table border="1"><tbody><tr>            <td>StatusCode</td>            <td>ReasonPhrase</td>            <td>說明</td>        </tr><tr>            <td>100</td>            <td>Continue</td>            <td>Client端有一個Message要發送給Server
但希望在發送之前先看一下Server是否會接受這個Message
所以在Request表頭中加入一個名稱Expect值為100 Conutinue
Server端收到後如果可以接受，就馬上回應這個狀態碼給Client
表示收到了Request的初始部份，要求Client端繼續
通常用於傳送接收一個大的Message時的優化</td>        </tr><tr>            <td>101</td>            <td>Switching Protocols</td>            <td>伺服器正在切換成Request封包表頭中
Update所指定的通訊協定</td>        </tr></tbody></table></div>

## 200~299 成功狀態碼
<div><table border="1"><tbody><tr>            <td>Status Code</td>            <td>Reason Phrase</td>            <td>說明</td>        </tr><tr>            <td>200</td>            <td>OK</td>            <td>就是OK</td>        </tr><tr>            <td>201</td>            <td>Created</td>            <td>資源已建立，用於回應建立資源的要求，例如PUT
回應的訊息中，應該在表頭中加入Location
用來告訴Client建立好的資源URL位置</td>        </tr><tr>            <td>202</td>            <td>Accepted</td>            <td>請求已被接受，但伺服器還未執行任何動作，也不能保證會完成
簡單的說，就是朕知道了...</td>        </tr><tr>            <td>203</td>            <td>Non-Authoritative
Information</td>            <td>Header中包含的訊息，並不是來自於要求的伺服器
而是來自資源的一個副本</td>        </tr><tr>            <td>204</td>            <td>No Content</td>            <td>用來告訴瀏覽器，在不轉頁的情況下，刷新表單頁面</td>        </tr><tr>            <td>205</td>            <td>Reset Content</td>            <td>用來告訴瀏覽器，Reset目前頁面中的表單元素</td>        </tr><tr>            <td>206</td>            <td>Partial Content</td>            <td>Client透過Request Header中的Range來要求部份或某個範圍的資源
這個狀態碼就是成功執行了一個部份或是某個範圍的請求
Response中的Header必須包含Content-Range、Date
以及ETag或是Content-Location</td>        </tr></tbody></table></div>

## 300~399 重轉向定位狀態碼
<div><table border="1"><tbody><tr>            <td>Status Code</td>            <td>Reason Phrase</td>            <td>說明</td>        </tr><tr>            <td>300</td>            <td>Multiple Choices</td>            <td>訊息類狀態碼</td>        </tr><tr>            <td>301</td>            <td>Moved Permanently</td>            <td>所要求的資源已移除，永久轉向
Response Header中的Location為新的URL
之前的要求都要改成新的URL
HTTP/1.0版本使用</td>        </tr><tr>            <td>302</td>            <td>Found</td>            <td>和301狀態碼類似
差別在於Header中Location給出的URL是暫時性的
之後的要求還是要用原來的URL</td>        </tr><tr>            <td>303</td>            <td>See Other</td>            <td>回應Client端另一個URL來獲得資源
主要目的是允許POST請求的回應轉向到某個資源</td>        </tr><tr>            <td>304</td>            <td>Not Modified</td>            <td>通過Client的Request Header來判斷
如果資源末被修改的話，就回應這個狀態碼</td>        </tr><tr>            <td>305</td>            <td>Use Proxy</td>            <td>必須通過一個代理來訪問資源
代理的位置由Header中的Location給出</td>        </tr><tr>            <td>306</td>            <td>尚未使用</td>            <td>該狀態碼目前尚未使用</td>        </tr><tr>            <td>307</td>            <td>Temporary Redirect</td>            <td>和301狀態碼類似
差別在於Header中Location給出的URL是暫時性的
之後的要求還是要用原來的URL
HTTP/1.1版本使用</td>        </tr></tbody></table></div>

## 400~499 客戶端錯誤狀態碼
<div><table border="1"><tbody><tr>            <td>Status Code</td>            <td>Reason Phrase</td>            <td>說明</td>        </tr><tr>            <td>400</td>            <td>Bad Request</td>            <td>告訴客戶端它發送了一個錯誤的要求</td>        </tr><tr>            <td>401</td>            <td>Unauthorized</td>            <td>告訴客戶端在要求資源之前，需要先經過身份驗證</td>        </tr><tr>            <td>402</td>            <td>Payment Required</td>            <td>目前尚未使用</td>        </tr><tr>            <td>403</td>            <td>Forbidden</td>            <td>告訴客戶端服務已被拒絕了
拒絕的原因可在回應的主體部份來描述
但這個狀態碼通常是不想說明拒絕原因的時後使用的</td>        </tr><tr>            <td>404</td>            <td>Not Found</td>            <td>找不到所要求的資源</td>        </tr><tr>            <td>405</td>            <td>Method Not Allowed</td>            <td>告訴客戶端收到不支援的HTTP Method
並在回應的表頭中以Allow告知可支援的Method</td>        </tr><tr>            <td>406</td>            <td>Not Acceptable</td>            <td>Client端可在表頭中用Accept告之可接受的資源型態
當Server端沒有所指定的資源型態時，用這個狀態碼來告之
通常會在回應的表頭中，加上一些訊息
讓Client端知道為什麼要求無法滿足</td>        </tr><tr>            <td>407</td>            <td>Proxy Authentication Required</td>            <td>和401狀態碼類似
但目標是要求對資源進行認證的代理伺服器</td>        </tr><tr>            <td>408</td>            <td>Request Timeout</td>            <td>完成要求的時間太長，伺服器所回應的狀態碼
並關閉連接
逾時時間以伺服器設定為主</td>        </tr><tr>            <td>409</td>            <td>Conflict</td>            <td>和訴客戶端，資源發出衝突</td>        </tr><tr>            <td>410</td>            <td>Gone</td>            <td>和404類似
只是伺服器曾經擁有該資源，只是被移除了</td>        </tr><tr>            <td>411</td>            <td>Length Required</td>            <td>告訴客戶端表頭中需要包含Content-Length</td>        </tr><tr>            <td>412</td>            <td>Preconditaion Failed</td>            <td>客戶端發起條件請求，其中一個條件失敗了的時後使用的回應碼</td>        </tr><tr>            <td>413</td>            <td>Request Entity Too Large</td>            <td>客戶端發送的Message比伺服器能夠處理的要大時
用這個狀態碼回應</td>        </tr><tr>            <td>414</td>            <td>Request URI Too Long</td>            <td>客戶端發送的URL比伺服器能夠處理的長度要長時
要這個狀態碼回應</td>        </tr><tr>            <td>415</td>            <td>Unsupported Media Type</td>            <td>伺服器無法支援客戶端發送的mime type時
用這個狀態碼回應</td>        </tr><tr>            <td>416</td>            <td>Requested Range Not Satisfiable</td>            <td>客戶端要求的表頭Range中指定了資源的某個範圍時
伺服器在範圍無效或是無法滿足時，用這個狀態碼回應</td>        </tr><tr>            <td>417</td>            <td>Expectation Failed</td>            <td>客戶端要求的表頭Expect中包含了一個期望時
伺服器無法滿足時，用這個狀態碼回應</td>        </tr></tbody></table></div>

## 500~599 伺服器端錯誤狀態碼
<div><table border="1"><tbody><tr>            <td>Status Code</td>            <td>Reason Phrase</td>            <td>說明</td>        </tr><tr>            <td>500</td>            <td>Internal Server Error</td>            <td>伺服器錯誤</td>        </tr><tr>            <td>501</td>            <td>Not Implemented</td>            <td>伺服器無法處理Client所發起的要求
例如使用了不支援的HTTP Method</td>        </tr><tr>            <td>502</td>            <td>Bad Gateway</td>            <td>代理或是Gateway收到了一條偽裝的回應
就會回應這個狀態碼</td>        </tr><tr>            <td>503</td>            <td>Service Unavailable</td>            <td>伺服器目前無法提供服務，例如過於忙錄
可以在Response Header中加入一個Retry-After
用來表示服務什麼時後會變為可用的</td>        </tr><tr>            <td>504</td>            <td>Gateway Timeout</td>            <td>和狀態碼408類似，只是這個的回應來自於一個Gateway或代理
它們在等待另一個伺服器對其請求時逾時了</td>        </tr><tr>            <td>505</td>            <td>HTTP Version Not Supported</td>            <td>伺服器收到不支援的通訊協定版本時的狀態回應碼</td>        </tr></tbody></table></div>