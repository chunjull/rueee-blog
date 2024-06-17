---
title: '#50 DOM：節點修改'
category: DoJS
tags:
  - JavaScript
abbrlink: 1334002290
date: 2023-12-13 00:00:00
---
透過節點修改，可以將新增的 DOM 節點加入到指定位置。
<!--more-->
## 快速了解
前面提過：新增的元素或節點需要藉由 `appendChild()` 、 `insertBefore()` 或 `replaceChild()` 等方法加入到指定位置，才能顯示。
這些方法可以將新建立的 DOM 節點置入到指定位置。
### Node.appendChild(childNode)
透過 `appendChild()` 可以將指定的 `childNode` 節點，加入到父容器節點的末端。
```html
<ul id="myList">
	<li>Item 01</li>
	<li>Item 02</li>
	<li>Item 03</li>
</ul>
```
```jsx
let myList = document.getElementById("myList");
let newList = document.createElement("li");
let textnode = document.createTextNode("Item 04");
newList.appendChild(textnode);
myList.appendChild(newList);
```
上述程式碼在取得容器後，會依序建立 `<li>` 元素與文字節點，再透過 `appendChild()` 將 `textNode` 加入到 `newList` ，最後，把 `newList` 置於 `myList` 的最後方，即可成功顯示。
### Node.insertBefore(newNode, refNode)
透過 `insertBefore()` 方法可以將新節點 `newNode` 插入到指定的 `refNode` 節點前面。
```html
<ul id="myList">
	<li>Item 01</li>
	<li>Item 02</li>
	<li>Item 03</li>
</ul>
```
```jsx
let myList = document.getElementById("myList");
let refNode = document.querySelectorAll("li")[1];
let newNode = document.createElement("li");
let textNode = document.createTextNode("Item 1.5");
newNode.appendChild(textNode);
myList.insertBefore(newNode, refNode);
```
上述程式碼在取得容器後，會取得 `<li>Item 02</li>` 元素並建立 `li` 元素和文字節點，再將 `newNode` 插入到 `refNode` 前方。
### Node.replaceChild(newChildNode, oldChildNode)
透過 `Node.replaceChild()` 可以將原本的 `oldChildNode` 替換成指定的 `newChildNode` 。
```html
<ul id="myList">
	<li>Item 01</li>
	<li>Item 02</li>
	<li>Item 03</li>
</ul>
```
```jsx
let myList = document.getElementById("myList");
let oldNode = document.querySelectorAll("li")[1];
let newNode = document.createElement("li");
let textNode = document.createTextNode("Item 002");
newNode.appendChild(textNode);
myList.replaceChild(newNode, oldNode);
```
上述程式碼在取得容器後，會取得 `<li>Item 02</li>` 元素並建立 `li` 元素和文字節點，再將原有的 `oldNode` 替換成新節點的 `newNode` 。
## 了解更多
- [Kuro－DOM Node 的建立、刪除與修改](https://ithelp.ithome.com.tw/articles/10191867)：本文最主要的參考範例。