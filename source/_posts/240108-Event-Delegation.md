---
title: '#76 事件指派'
category: DoJS
tags:
  - JavaScript
abbrlink: 3886780583
date: 2024-01-08 00:00:00
---
事件指派會將目標元素的「父級」綁定監聽，再透過冒泡機制傳遞。
<!--more-->
## 快速了解
事件指派（Event Delegation）是利用「事件流程」及「單一事件監聽器」來處理多個事件目標。如此不只能提高效率，也能處理動態新增的問題。
直接對目標的父元素進行事件監聽，透過冒泡機制，事件會由父元素傳遞到底下的所有子元素，就不需對子元素事件一個個監聽。
### 事件指派範例
```html
<ul id="myList">
	<li>Item 01</li>
	<li>Item 02</li>
	<li>Item 03</li>
</ul>
```
在不透過事件指派的情況下，如果要分別為 `myList` 的 `li` 綁定 `click` 事件，就要利用 `for` 迴圈一個個綁定。
但這時若是要再新增元素到 `myList` ，會導致「後來新增的 `newList` 節點不會被註冊 `click` 事件」的問題。
如果每次新增元素後要再重新註冊 `addEventListener` ，可能會因為重複監聽且忘了移除監聽，而導致記憶體流失（memory leak）的問題。
這時，可以藉由事件指派的方法來解決該問題：
```jsx
let myList = document.getElementById("myList");
myList.addEventListener("click", function(e){
	if(e.target.tagName.toLowerCase() === "li"){
		console.log(e.target.textContent);
	}
}, false);

let newList = document.createElement("li");
let textNode = document.createElement("Hello World!");
newList.appendChild(textNode);
myList.appendChild(newList);
```
上述程式碼中，在取得容器並讓外層 `myList` 來監聽 `click` 事件後，使用 `if` 判斷式判斷目標元素是否為 `li` ，若是，則執行 `console.log` 。接著，建立新的 `<li>` 元素及 `textNode` 文字節點，再透過 `appendChild` 將 `textNode` 加入到 `newList` 中，最後，透過 `appendChild` 將  `newList` 加入至 `myList` 。
把 `click` 事件改由外層的 `myList` 監聽，利用事件傳遞的原理，判斷 `e.target` 是目標節點後，再去執行後續動作。這麼做的好處是：可以輕鬆管理事件，且無需再為後續新增的 `newList` 額外綁定 `click` 事件。
### 小知識
- Event Delegation 又翻譯為「事件代理」、「事件委派」。
## 了解更多
- [Kuro－隱藏在 "事件" 之中的秘密](https://ithelp.ithome.com.tw/articles/10192015)：本文最主要的參考範例。
- [Teagan Hsu－DOM事件、Event Delegation](https://teagan-hsu.coderbridge.io/2021/01/01/javascript-dom-event-and-event-delegation/)：複習 DOM 事件。