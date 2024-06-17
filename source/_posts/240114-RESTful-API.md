---
title: '#82 RESTful API'
category: DoJS
tags:
  - JavaScript
abbrlink: 3768071640
date: 2024-01-14 00:00:00
---
RESTful API 是一種「語意化且寫法一致」的程式設計風格。
<!--more-->
## 快速了解
REST（Representational State Transfer），被譯為「表現層狀態轉換」。
是一種程式設計風格，而非標準，以語意化且更為嚴謹的方式描述 API，以此風格設計的架構被稱為「RESTful」。
### RESTful API 的特性
RESTful API 具有靈活、可擴展且高度獨立的優點，而受到開發者歡迎。
且擁有以下幾種特性：
- 統一介面：API 的設計要盡可能簡單且一致。
- 無狀態：每一個請求都是獨立的，服務器不會儲存任何請求的狀態。
- 分層系統：可以使用代理伺服器進行轉發，或提供安全性控制等。
- 可緩存：響應中的資料能夠被客戶端緩存，提高性能。
- 隨需編碼：伺服器可透過將程式碼傳輸至用戶端，以臨時擴展或自訂用戶端功能。
### RESTful API 運作流程
RESTful API 的呼叫流程：
1. 用戶端按照 API 文件，以格式化方式向伺服器端傳送請求。
2. 伺服器端對用戶端進行身份驗證，並確認用戶端有權發出請求。
3. 伺服器端接收請求，並在內部處理。
4. 伺服器端向用戶端傳送回應，該回應包含用戶端請求的任何資訊。
### RESTful API 範例
RESTful 風格的網址設計強調**從路由結構就能看出要對什麼資料、進行什麼操作**。
一般的 API 可能會長這樣：
```jsx
新增使用者：POST + /new_user
刪除使用者：POST + /delete_user
查詢使用者：GET + /user_data/:id
更改使用者：POST + /update_user
```
RESTful API 則會長這樣：
```jsx
新增使用者：POST + /users
刪除使用者：DELETE + /users/:id
查詢使用者：GET + /users/:id
更改使用者：PATCH + /users/:id
```
透過把「動作」藏在 HTTP method 裡面，而有唯一的 URL（ `/users` ）表示資源位置，藉此統一 API 接口。
## 了解更多
- [AWS－什麼是 RESTful API？](https://aws.amazon.com/tw/what-is/restful-api/)：深入了解 RESTful API 的使用方式。
- [ALPHAcamp－什麼是REST? 認識 RESTful API 路由語義化設計風格](https://tw.alphacamp.co/blog/rest-restful-api)：了解 RESTful API 的意義。
- [itsems－API 是什麼? RESTful API 又是什麼?](https://medium.com/itsems-frontend/api-是什麼-restful-api-又是什麼-a001a85ab638)：了解 API 和 RESTful API 的差異。