---
title: '#51 DOM：節點刪除'
category: DoJS
tags:
  - JavaScript
abbrlink: 2687438073
date: 2023-12-14 00:00:00
---
`removeChild()` 可以移除單一節點； `innerHTML` 則可以清空所有內容。
<!--more-->
## 快速了解
DOM 除了新增、修改等功能，還可以刪除節點。
透過 `removeChild()` 方法，可以將指定的 `childNode` 子節點刪除。
```html
<ul id="myList">
	<li>Item 01</li>
	<li>Item 02</li>
	<li>Item 03</li>
</ul>
```
```jsx
let myList = document.getElementById("myList");
let removeNode = document.querySelectorAll("li")[1];
myList.removeChild(removeNode);
```
上述程式碼在取得容器後，會先取得 `<li>Item 02</li>` 元素，再將 `myList` 下的 `removeNode` 節點刪除。
### 清空元素的內容
 `removeChild()` 只能移除單一的網頁節點，如果需要將某個元素的內容清空，可以使用 `innerHTML` ，就可以輕鬆將 `myList` 裡面的 HTML 一口氣清空。
```jsx
myList.innerHTML = "";
```
## 了解更多
- [Kuro－DOM Node 的建立、刪除與修改](https://ithelp.ithome.com.tw/articles/10191867)：本文最主要的參考範例。