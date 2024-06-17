---
title: '#53 DOM：文字節點'
category: DoJS
tags:
  - JavaScript
abbrlink: 434066502
date: 2023-12-16 00:00:00
---
`textContent` 回傳純文字，而 `innerText` 則會回傳實際呈現在頁面上的樣子。
<!--more-->
## 快速了解
透過 `textContent` 與 `innerText` 可以選取並新增、修改、刪除文字節點。
這兩者用途很相似，但仍有所區別。
### textContent
 `textContent` 會獲取節點中所有元素的內容，包括 `<script>` 與 `<style>` 元素。
且回傳節點中的每一個元素，故隱藏內容仍會在畫面中顯示，例如：下面案例的 `<span style="display:none;">!!!</span>` 。
```html
<h1>hello world</h1>
<p>hello world<span style="display:none;">!!!</span></p>
```
```jsx
const h1 = document.querySelector("h1");
console.log(h1.textContent); // "hello world"
const el = document.querySelector("p");
console.log(el.textContent); // "hello world!!!"
```
### innerText
 `innerText` 會獲取「渲染後的文字內容」（rendered text content），即被 CSS 調整過樣式的文字。
受 CSS 樣式影響，只會展示「實際所見的內容」，不會回傳隱藏元素的內容，且會觸發回流。
```html
<h1>hello world</h1>
<p>hello world<span style="display:none;">!!!</span></p>
```
```jsx
const h1 = document.querySelector("h1");
console.log(h1.textContent); // "hello world"
const el = document.querySelector("p");
console.log(el.textContent); // "hello world"
```
## 了解更多
- [MDN－innerText](https://developer.mozilla.org/zh-TW/docs/Web/API/HTMLElement/innerText)：了解 `innerText` 的概念。
- [MDN－textContent](https://developer.mozilla.org/zh-CN/docs/Web/API/Node/textContent)：了解 `textContent` 的概念。
- [Eason Lin－innerText 與 textContent](https://uu9924079.medium.com/javascript%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98-innertext-%E8%88%87-textcontent-755b8b93f13b)：了解 `innerText` 與 `textContent` 的差異。