---
title: '#49 DOM：節點新增'
category: DoJS
tags:
  - JavaScript
abbrlink: 929725069
date: 2023-12-12 00:00:00
---
針對不同元素、節點，DOM 有不同的新增方式。
<!--more-->
## 快速了解
### 新增元素
使用 `document.createElement()` 可以建立一個新元素。
透過這個方式新增的元素，還需要藉由 `appendChild()` 、 `insertBefore()` 或 `replaceChild()` 等方法將其加入到指定位置，才能顯示。
例如：針對新建立的 `newDiv` 元素加入指定的 `id` 與 `class` 屬性。
```jsx
let newDiv = document.createElement("div");
newDiv.id = "myNewDiv";
newDiv.className = "box";
document.body.appendChild(newDiv);
```
上述程式碼會建立一個新的 `div` 元素，再添加到 <body> 的最尾部。
### 新增文字節點
使用 `document.createTextNode()` 可以建立文字節點，在括號內加入字串即可。
和 `document.createElement()` 一樣，這個新增的文字節點在被加入到某個節點前，在瀏覽器上看不到。
```jsx
let newDiv = document.createElement("div");
let textNode = document.createTextNode("Hello World!");
newDiv.appendChild(textNode);
```
### 新增 DocumentFragment
 `DocumentFragment` 是一種特殊的 DOM 節點，它是沒有父層節點的「最小化文件物件」。可以將其視為一個輕量化的 `document` ，用如同標準文件一般的方法來保存「片段的文件結構」。
```html
<ul id="myList"></ul>
```
```jsx
let ul = document.getElementById("myList");
let fragment = document.createDocumentFragment();
for (let i = 0; i < 3; i++){
	let li = document.createElement("li");
	li.appendChild(document.createTextNode("Item" + (i + 1)));
	fragment.appendChild(li);
};
ul.appendChild(fragment);
```
上述程式碼會建立一個「有三個項目的列表清單」。
### document.write()
使用 `document.write()` 不只可以新增字串和 HTML 標籤，甚至可以加入 `<script>` 標籤。
當網頁已經讀取完成後，才會執行 `document.write()` 並將內容輸出，這時新增的內容會完全覆蓋掉目前的網頁。
```jsx
// 新增 HTML 標籤
document.write("<h1>Hello World!</h1>");
// 新增 <script> 標籤
document.write("<script type=\"text\javascript\" src=\"file.js\">" + "<\/script>");
```
### 小知識
- 因為 `DocumentFragment` 不是真實的 DOM 結構，所以它的變動不會影響目前的網頁文件，也不會導致回流（reflow）或引起任何影響效能的情況。因此，當需要進行大量的 DOM 操作時，用 `DocumentFragment` 的效能會比較高。
- 不建議使用 `document.write()` 語法，詳情可參見 [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document/write) 與 [stackoverflow](https://stackoverflow.com/questions/802854/why-is-document-write-considered-a-bad-practice)。
## 了解更多
- [Kuro－DOM Node 的建立、刪除與修改](https://ithelp.ithome.com.tw/articles/10191867)：本文最主要的參考範例。
- [MDN－DocumentFragment](https://developer.mozilla.org/zh-TW/docs/Web/API/DocumentFragment)：了解 `DocumentFragment` 的概念。
- [ExplainThis－回流 (Reflow) 和重繪 (Repaint) 是什麼？](https://www.explainthis.io/zh-hant/swe/repaint-and-reflow)：了解瀏覽器渲染的概念。