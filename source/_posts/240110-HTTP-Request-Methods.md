---
title: '#78 HTTP 請求方法'
category: DoJS
tags:
  - JavaScript
abbrlink: 842599140
date: 2024-01-10 00:00:00
---
用戶端會依據 HTTP 請求方法向伺服器端溝通。
<!--more-->
## 快速了解
HTTP 定義了一組能以不同方式操作指定資源的請求方法（request methods），讓伺服器端能夠清楚辨識 request 的目的。
### HTTP 請求方法
HTTP 總共有九種請求方法：

| 請求方法 | 說明 |
| --- | --- |
|  GET  | 只應用於取得資料。 |
|  HEAD  | 與 GET 方法相同的回應，但只獲取回應的 header，而沒有 body。 |
|  POST  | 用於提交指定資源的實體，通常會改變伺服器的狀態。 |
|  PUT  | 取代原本的整個 request。和 PATCH 類似。 |
|  DELETE  | 刪除指定資源。 |
|  CONNECT  | 會和指定資源標明的伺服器之間，建立隧道（tunnel）。 |
|  OPTIONS  | 會回傳指定資源其支援哪些請求方法。 |
|  TRACE  | 會與指定資源標明的伺服器之間，執行迴路返回測試（loop-back test）。 |
|  PATCH  | 修改指定資源的部分 request。 |

### CRUD 原則
常用的幾個動作分別為： `GET` / `POST` / `PUT` / `DELETE`，正好對應到資料庫基本操作：CRUD 增刪查改：

| 請求方法 | 操作方式 | 說明 |
| --- | --- | --- |
|  POST  | Create | 新增、建立。 |
|  GET  | Read | 查詢、讀取。 |
|  PUT  | Update | 更新。 |
|  DELETE  | Delete | 刪除。 |

### GET & POST 請求的區別
 `GET` 和 `POST` 兩種是最常使用的 HTTP 請求方法，兩者最直觀的區別是「資料傳遞方式」與「安全性」。
- `GET` ：向指定的資源要求資料，類似於查詢操作。
    - 資料傳遞方式：將引數由 URL 帶至伺服器端。
    - 安全性：較 `POST` 不安全，因為傳遞的引數會在 URL 上顯示。
    - 例如：讀取連結或圖片。
- `POST` ：將要處理的資料提交給指定的資源，類似於更新操作。
    - 資料傳遞方式：將引數放在 request body 中傳遞。
    - 安全性：較 `GET` 安全，適合用於隱密性較高的資料。
    - 例如：會員登入系統。
### 小知識
- `HEAD` 較少使用，通常應用在只想知道 response 資訊時。
## 了解更多
- [MDN－HTTP 請求方法](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Methods)：了解 HTTP 請求方法。
- [維基百科－增刪查改](https://zh.wikipedia.org/wiki/增刪查改)：了解 CRUD 的意義。