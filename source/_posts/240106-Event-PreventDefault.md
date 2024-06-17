---
title: '#74 阻擋預設行為'
category: DoJS
tags:
  - JavaScript
abbrlink: 1726339634
date: 2024-01-06 00:00:00
---
`e.preventDeault()` 可以取消事件的預設行為，但不會影響該事件傳遞。
<!--more-->
## 快速了解
部分 HTML 元素會有預設行為，例如： `<a>` 的連結、表單的 `<submit>` ，如果需要在這些元素上綁定事件，就可能會需要適當地取消它們的預設行為。
透過在 Event Handler 加上 `e.preventDeault()` 的方式即可阻擋預設行為。
### 阻擋預設行為範例
假設要在一個通往 google 的連結 `<a>` 註冊 `click` 事件，當點擊該連結時，會印出 `Google!` 的內容，而不會直接連結到 google 網站。
```html
<a id="link" href="https://www.google.com">Google</a>
```
```jsx
var link = document.querySelector("#link");
link.addEventListener("click", function(e){
	e.preventDefault();
	console.log("Google!");
}, false);
```
在 Event Handler 加上 `e.preventDeault()` 即可阻擋預設行為，讓 `<a>` 元素的預設行為失效，並讓瀏覽器執行開發者註冊的函式內容。
### 小知識
- `event.preventDefault()` 不會阻止事件向上傳遞（事件冒泡）。
## 了解更多
- [Kuro－隱藏在 "事件" 之中的秘密](https://ithelp.ithome.com.tw/articles/10192015)：本文最主要的參考範例。
- [MDN－preventDefault](https://developer.mozilla.org/zh-TW/docs/Web/API/Event/preventDefault)：了解 `e.preventDeault()` 的使用方式。