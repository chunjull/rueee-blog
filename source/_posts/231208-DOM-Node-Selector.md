---
title: '#45 DOM：節點選取'
category: DoJS
tags:
  - JavaScript
abbrlink: 747586579
date: 2023-12-08 00:00:00
---
DOM 有多種選取方式，例如：標籤名稱、class、id、選擇器等。
<!--more-->
## 快速了解
常見的 DOM 選取方法有以下幾種：

針對給定的 tag 名稱，回傳所有符合條件的集合。
```jsx
document.getElementsByTagName("name");
```

針對給定的 class 名稱，回傳所有符合條件的集合。
```jsx
document.getElementsByClassName("name");
```

針對給定的 Selector 名稱，回傳第一個符合條件的集合。
```jsx
document.querySelector("name");
```

針對給定的 Selector 名稱，回傳所有符合條件的集合。
```jsx
document.querySeletorAll("name");
```
### 節點選取範例
試著在 HTML 檔案中選取 `h1` 標籤。
```html
<body>
	<h1 class="header">Hello!</h1>
	<a href="#">Link</a>
</body>
```
```jsx
const element = document.querySeletor("h1");
console.log(element); // <h1 class="header">Hello!</h1>
```
### 小知識
- `document.querySelector` 與 `document.querySeletorAll` 可以用「CSS 選擇器」來取得「第一個」或「所有」符合條件的元素集合（NodeList）。
## 了解更多
- [Kuro－透過 DOM API 查找節點](https://ithelp.ithome.com.tw/articles/10191765)：本文最主要的參考範例。
- [MDN－CSS 選擇器](https://developer.mozilla.org/zh-TW/docs/Glossary/CSS_Selector)：了解 CSS 選擇器的概念。