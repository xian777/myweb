---
title: HTTP Method
tags:
  - HTTP
date: 2013-08-16 14:37:00
---

# HTTP Method
<div><table border="1"><tbody><tr>            <td>GET</td>            <td>這是最常用的方法，通常用在請求伺服器上的某個資源
該方法沒有Body主體，可以被Cache
HTTP protocols中並沒有規範長度限制，有限制的是瀏覽器和Web Server
不同瀏覽器中的限制也不同，IE為2048，FF為8192</td>        </tr><tr>            <td>POST</td>            <td>向伺服器輸入數據，通常會以透過表單的方式
資料會在HTTP Body的部份，以name=value的方式表示，分隔符號為&amp;
該方法不會被Cache</td>        </tr><tr>            <td>PUT</td>            <td>將資源寫入伺服器端，如果資源已存在，就用這個資源來取代原有的資源
因為需要對伺服器寫入，所以基本上都需要先通過身份驗證是否有寫入的權限
寫入成功後，應回應201，並在表頭中用Location告訴Client端寫入的資源位置</td>        </tr><tr>            <td>DELETE</td>            <td>要求伺服器刪除指定的資源</td>        </tr><tr>            <td>PATCH</td>            <td>要求伺服器更新指定的資源</td>        </tr><tr>            <td>HEAD</td>            <td>和GET方法的行為很類似，但在伺服器端回應的訊息中，只包含HTTP Header而已
並不會返回HTTP Body的部份，適用於在不取得資源的情況下，了解資源的狀態</td>        </tr><tr>            <td>TRACE</td>            <td>要求伺服器返回接收到的表頭資料
用意是用來追蹤發送出去的表頭，和到伺服器接收到的表頭，有何差異</td>        </tr><tr>            <td>OPTIONS</td>            <td>要求伺服器返回可接收的HTTP Method指令有那些
因為並不是所有Method都有被Web Server所實作</td>        </tr></tbody></table></div>