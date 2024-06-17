---
title: '#85 Ajax：處理方式'
category: DoJS
tags:
  - JavaScript
abbrlink: 2744536984
date: 2024-01-17 00:00:00
---
XMLHttpRequest、Fetch、axios 都是 Ajax 的處理方式。
<!--more-->
## 快速了解
一般來說，Ajax 的處理方式有三種：
1. XMLHttpRequest。
2. Fetch。
3. axios。
前兩者是原生 JS 寫法，最後的 axios 則是需要額外安裝的 JS 套件。
### XMLHttpRequest
最早期的 Ajax 會使用 XMLHttpRequest 物件（簡稱「XHR」）實作非同步請求，例如以下範例：
```jsx
function reqListener(){
	console.log(this.responseText);
}
var oReq = new XMLHttpRequest();
oReq.addListener("load", reqListener);
oReq.open("GET", "http://www.example.org/example.txt");
oReq.send();
```
在上述程式碼中，為了送出 HTTP 請求，需要先建立一個 XMLHttpRequest 物件，並使用 `.open()` 開啟一個 URL，最後再用 `.send()` 發出 request。
因為使用 XHR 步驟繁多、較麻煩，實務上很少直接使用原生的 XMLHttpRequest。通常會透過 Fetch、axios 等方法取代。
### Fetch
原生 JS 還有另一個方法可以處理 Ajax：Fetch API。
```jsx
fetch("http://example.com/movies.json");
	.then(function(response){
		return response.json();
	})
	.then(function(myJson){
		console.log(myJson);
	});
```
使用 Fetch API 的方法會需要「先把回傳的檔案轉檔成 JSON 格式」，再執行後續程式碼。
### axios
axios 是一種 JS 套件，較上述兩者語法精簡、可以透過 node.js 整合後端且受到多種瀏覽器支援。
```jsx
axios.get('/user/12345')
	.then(function(response){
		console.log(response);
	});
```
上述程式碼中，axios 會藉由 `get` 向目標檔案取得資訊。
### 小知識
- 事實上，axios 還是透過 XMLHttpRequest 的方式實作 Ajax。
## 了解更多
- [MDN－XMLHttpRequest](https://developer.mozilla.org/zh-TW/docs/Web/API/XMLHttpRequest_API/Using_XMLHttpRequest)：了解 XMLHttpRequest 的處理方式。
- [MDN－Fetch](https://developer.mozilla.org/zh-TW/docs/Web/API/Fetch_API/Using_Fetch)：了解 Fetch 的處理方式。
- [oxxo－JavaScript Fetch API 使用教學](https://www.oxxostudio.tw/articles/201908/js-fetch.html)：觀看更多 Fetch 的使用範例。
- [Alysa Chen－axios基本語法與練習(GET、POST請求)](https://ithelp.ithome.com.tw/articles/10253259)：了解 axios 的處理方式。
- [GitHub－axios](https://github.com/axios/axios)：axios 官方文檔。