---
title: '#47 DOM：節點關係'
category: DoJS
tags:
  - JavaScript
abbrlink: 3807371373
date: 2023-12-10 00:00:00
---
DOM 節點是階層架構，有父子關係與兄弟關係兩種。
<!--more-->
## 快速了解
DOM 節點有分層的概念，大致可以把節點之間的關係分成兩種：
- 父子關係：除了 `document` 之外，每一個節點都會有個上層的節點，稱之為「父節點」（Parent node）；相對地，從屬於自己上層的節點被稱為「子節點」（Child node）。
- 兄弟關係：有同一個「父節點」的節點們，彼此之間互為「兄弟節點」（Sibling node）。
### 父子關係
- Node.childNodes：可以取得子元素，回傳值可能會是元素節點、文字節點（包括空白）或註解節點。
- Node.firstChild：可以取得 `Node` 節點的**第一個**節點，若無子節點則回傳 `null` 。
- Node.lastChild：可以取得 `Node` 節點的**最後一個**節點，若無子節點則回傳 `null` 。
- Node.parentNode：可以取得父元素，回傳值可能會是一個元素節點、根節點或 DocumentFragment 節點。
### 兄弟關係
- Node.previousSibling：可以取得同層之間的**前一個**節點，若已是第一個節點則回傳 `null` 。
- Node.nextSibling：可以取得同層之間的**後一個**節點，若已是最後一個節點則回傳 `null` 。
### 節點查找遍歷範例
試著透過以下範例，檢驗自己對「節點查找遍歷」的了解：
```html
<body>
	<h1>Title</h1>
	<div>
		<p><span>1</span><span>2</span><span>3</span></p>
		<a href="#">Link</a>
	</div>
</body>
```
```jsx
var h1 = document.querySelector("h1");
var div = document.querySelector("div");
var p = document.querySelector("p");
var span2 = document.querySelectorAll("span")[1]; // 第二個符合條件的元素

console.log(div.hasChildNodes()); // true
console.log(div.firstChild.tagName); // undefined
console.log(p.firstChild.tagName); // "SPAN"
console.log(p.lastChild.textContent); // "3"
console.log(h1.parentNode.nodeName); // "NODE"
console.log(span2.previousSibling.textContent); // "1"
console.log(span2.nextSibling.textContent); // "3"
```
### 小知識
- 基本上，隔層的節點沒有關係，所以並沒有爺孫節點、表堂兄弟節點這種存在。
- NodeList 物件常被誤認為是陣列，雖然它同樣帶有 `length` 屬性且可以透過 `[]` 加上索引的方式來存取，但它只是一個特殊的「物件」，而不是陣列，因此原生陣列方法不適用於 NodeList 物件上。
- `Node.firstChild` 和 `Node.lastChild` 的子節點包括「空白」節點。
- `Node.textContent` 會回傳目標的字串內容或 `null` 。
## 了解更多
- [Kuro－透過 DOM API 查找節點](https://ithelp.ithome.com.tw/articles/10191765)：本文最主要的參考範例。
- [MDN－NodeList](https://developer.mozilla.org/zh-TW/docs/Web/API/NodeList)：了解 NodeList 物件的概念。