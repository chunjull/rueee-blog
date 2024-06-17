---
title: '#55 DOM：標籤屬性'
category: DoJS
tags:
  - JavaScript
abbrlink: 1392055196
date: 2023-12-18 00:00:00
---
透過 `setAttribute` 可以為標籤設定屬性。
<!--more-->
## 快速了解
DOM 中也有針對標籤屬性的相關語法： `setAttribute` 。
### setAttribute
針對指定元素去設定標籤屬性，若屬性已經存在，會更新該值；否則會為指定的名稱和值添加一個新屬性。
 `setAttribute` 的語法為 `element.setAttribute(name, value);` ，第一個參數為屬性名稱，第二個參數為屬性值。
```html
<p>Something...</p>
```
```jsx
let el = document.querySelector("p");
el.setAttribute("color", "red");
```
上述程式碼會把 `color: red;` 的屬性加入到 `<p>` 標籤上。
### 補充用法
如果想獲取某個屬性目前的值，可以使用 `getAttribute()` ；而若想刪除某屬性，則可使用 `removeAttribute()` 。
此外，還可以透過 `hasAttribute()` 檢查指定屬性是否存在。
```jsx
let warning = el.getAttribute("color");
alert(warning); // red
console.log(el.hasAttribute("color")); // true
el.removeAttribute("color");
console.log(el.hasAttribute("color")); // false
```
## 了解更多
- [MDN－setAttribute](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/setAttribute)：了解 `setAttribute` 的概念。
- [MDN－getAttribute](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/getAttribute)：了解 `getAttribute` 的概念。