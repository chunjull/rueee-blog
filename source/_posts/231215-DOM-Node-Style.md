---
title: '#52 DOM：節點樣式'
category: DoJS
tags:
  - JavaScript
abbrlink: 2022605776
date: 2023-12-15 00:00:00
---
可以透過 JS 修改 CSS 樣式，但盡量不要這麼做。
<!--more-->
## 快速了解
JS 有以下幾種常見的修改 CSS 樣式方法：
- 直接修改元素的 `style` 屬性。
- 透過修改 `className` 屬性或 `classList` 提供的 api 來修改元素的 class 屬性。
- 利用 JS 直接寫入 CSS 樣式。
### 修改元素的 style 屬性
JS 修改元素的 style 屬性是對「行內樣式」進行修改。
是透過 DOM api 修改元素的行內樣式，因此，樣式優先級會高過多數的其他樣式寫法（ `!important` 除外）。
```html
<div class="box"></div>
```
```jsx
let box = document.querySelector(".box");
box.style.width = "50px";
box.style.height = "50px";
box.style.backgroundColor = "blue";
```
特別注意！JS 的變數名稱及物件屬性名不允許使用 `-` 符號，所以在使用時要改為「駝峰式」寫法。
### 修改元素的 class 屬性
由於 `class` 是保留的關鍵字，所以 JS 實際上是透過 `className` 來操作網頁標籤內的 `class` 屬性。
```html
<article id="article" class="small-font"> ... </article>
```
```jsx
let article = document.querySelector("#article");
article.className = "large-font";
// 執行結果
// <article class="large-font"> ... </article>
```
但是，當有多組 class 時，直接修改 `className` 內的值，不會保留原本的 `class` 屬性，原本的 class 會被覆蓋。為了解決這個問題， DOM api 新增了一組 `classList` 屬性來取代原本的 `className` ，讓原本的 `class` 屬性被保留。
元素裡的 `classList` 屬性與 `className` 不同的是：它是一個「唯獨」的屬性。換言之，不能直接透過變更這個屬性來修改 DOM 的 `class` ，而是要利用 `classList.add()` 與 `classList.remove()` 修改它。
```html
<article class="article small-font"> ... </article>
```
```jsx
let article = document.querySelector(".article");
article.classList.remove("small-font");
article.classList.add("large-font");
// 執行結果
// <article class="article large-font"> ... </article>
```
### 利用 JS 直接寫入 CSS 樣式
常見的做法有兩種：

利用 `document.write` 在 `<head>` 寫入 CSS。
```html
document.write("<style>element {...}</style>");
document.write("<link rel="stylesheet" href="xxx.css" />");
```

利用 `document.createElement` 新增 `link` 標籤。
```jsx
let head = document.querySelector("head");
let linkTag = document.createElement("link");
if (...) {
	linkTag.rel = "stylesheet";
	linkTag.type = "text/css";
	linkTag.href = "xxx.css";
	head.appendChild(linkTag);
};
```
透過這種方法的好處是：可以加入條件判斷來決定是否寫入 CSS 樣式。
### 小知識
- 通常來說，該交給 CSS 處理的樣式，就盡量不要用 JS 處理。
- CSS 分為行內樣式（inline-style）與外部樣式（external），前者是直接在 HTML 元素的 `style` 屬性進行設定；後者則會透過 `<link>` 連接外部 CSS 檔案。
- 事實上，直接利用 JS 直接寫入 CSS 樣式是比較少見的做法，但在某些情況下確實是個實用的方式。
## 了解更多
- [Greta Ma－如何用 JS 更改 HTML & CSS 屬性](https://ithelp.ithome.com.tw/articles/10218025)：了解動態更改元素樣式的方法。