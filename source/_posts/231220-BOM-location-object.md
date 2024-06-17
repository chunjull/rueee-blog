---
title: '#57 BOM：location'
category: DoJS
tags:
  - JavaScript
abbrlink: 1229262100
date: 2023-12-20 00:00:00
---
利用 `location` 可以擷取網址內容並進行換頁。
<!--more-->
## 快速了解
 `window.location` 物件包含了所有與目前頁面網址相關的資訊。
### 網址列結構
從網址列來看，由前到後分別是 `protocol` 、 `host` 、 `hostname` 、 `port` 、 `pathname` 、 `search` 、 `hash` 及包含整個網址的 `href` 屬性。
### 換頁方式
利用 JS 更換網址到新頁面有兩種方式： `location.href` 與 `location.replace()` ，兩者看似幾乎一樣，但仍有些差異。
 `location.href` 的範例：
```jsx
location.href = "https://www.google.com";
```
透過 `location.href` 換頁，就像是用滑鼠點擊 `<a>` 標籤的超連結一樣。瀏覽器會記錄該連結的歷史紀錄，所以可以藉由按下瀏覽器的「上一頁」、「下一頁」來進行來回。且可以使用 `document.referrer` 查到上一頁的來源網址。
 `location.replace()` 的範例：
```jsx
location.replace("https://www.google.com");
```
若是透過 `location.replace()` 來換頁，雖然在 `document.referrer` 同樣可以記錄上一頁的網址，但瀏覽器的歷史紀錄不會留存前一頁的紀錄，故無法透過瀏覽器的「上一頁」、「下一頁」按鈕來回跳頁。
### <a> 標籤
DOM 裡的 `<a>` 元素也有提供類似 `location` 的屬性。
如果要擷取某個網址的 `hostname` 、 `pathname` 、 `query string` 及 `hash` 等值，如果透過傳統做法，會使用「正規表示法」（Reglar Expression）擷取該網址的字串並進行解析，但也可以使用更簡潔的方式透過 `<a>` 標籤解析：
```jsx
let link = document.createElement("a");
link.href = "https://example.org:8080/foo/bar?q=baz#bang";
console.log(link.hostname); // 'example.org'
console.log(link.pathname); // '/foo/bar'
console.log(link.hash); // '#bang'
```
利用 `document.createElement` 建立 `<a>` 標籤，再透過 `href` 屬性將網址傳入 `link` 後，這個 `link` 變數也跟 `location` 物件擁有同樣屬性的結構，因此，可以直接對該變數擷取需要的值。
### 小知識
- 可以透過指定 `hash` 屬性跳到指定錨點。
## 了解更多
- [MDN－location](https://developer.mozilla.org/en-US/docs/Web/API/Location)：了解 `location` 的概念，內有範例網址可參考結構。
- [MDN－Document.referrer](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/referrer)：了解 `document.referrer` 的概念。
- [Huli－簡易 Regular Expression 入門指南](https://blog.huli.tw/2020/05/16/introduction-to-regular-expression/)：了解 Reglar Expression 的基礎寫法。