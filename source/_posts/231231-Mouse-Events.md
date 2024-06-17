---
title: '#68 滑鼠相關事件'
category: DoJS
tags:
  - JavaScript
abbrlink: 3660518762
date: 2023-12-31 00:00:00
---
滑鼠相關事件觀念不難，卻非常重要，是常見面試考題。
<!--more-->
## 快速了解
以下為幾種常見的滑鼠相關事件：
- `mousedown` / `mouseup` 事件：此二事件分別會在滑鼠點擊某元素「按下」（mousedown）按鈕，及「放開」（mouseup）按鈕時觸發。
- `click` 事件：當滑鼠「點擊」某元素時觸發。
- `dbclick` 事件：當滑鼠「連點兩次」某元素時觸發。
- `mouseenter` / `mousemove` / `mouseleave` / `mouseover` 事件：這幾個事件要放在一起看
    1. 當滑鼠游標移入某元素時，會先觸發 `mouseenter` / `mouseover` 事件。
    2. 滑鼠游標在這個元素內「移動」時，會連續觸發 `mousemove` 事件。
    3. 直到滑鼠游標離開該元素，才觸發 `mouseleave` 事件。
### mouseenter v.s. mouseover
 `mouseenter` / `mouseover` 事件雖然都是滑鼠游標移入了某元素時觸發，但兩者最大的不同之處，在於支援事件冒泡與否，以及觸發時間的不同。
首先，說明兩者冒泡與否的差異。
```html
<div class="outer">
	<div class="inner"></div>
</div>
```
先看看為 `inner` 與 `outer` 註冊 `mouseenter` 事件的回傳結果：
```jsx
let outer = document.querySelector(".outer");
let inner = document.querySelector(".inner");
outer.addEventListener("mouseenter", function(){
	console.log("outer");
}, false);
inner.addEventListener("mouseenter", function(){
	console.log("inner");
}, false);

// "outer"
// "inner"
```
再看看註冊 `mouseover` 事件的回傳結果：
```jsx
let outer = document.querySelector(".outer");
let inner = document.querySelector(".inner");
outer.addEventListener("mouseover", function(){
	console.log("outer");
}, false);
inner.addEventListener("mouseover", function(){
	console.log("inner");
}, false);

// "outer"
// "inner"
// "outer"
```
 `mouseover` 事件與 `mouseenter` 的差異在於： `mouseover` 會將事件冒泡至上層元素當中。換句話說，當 `inner` 的 `mouseover` 事件被觸發了，它同時也會將事件傳遞一份到上層元素中，即 `outer` ，因此 console 會再次印出 `"outer"` 。
接著，說明兩者觸發時間的差異。
在下面案例中，同時為 `outer` 註冊 `mouseenter` 與 `mouseover` 事件：
```jsx
let outer = document.querySelector(".outer");
outer.addEventListener("mouseenter", function(){
	console.log("outer - mouseenter");
}, false);
outer.addEventListener("mouseover", function(){
	console.log("outer - mouseover");
}, false);

// "outer - mouseover"
// "outer - mouseenter"
```
由此可以觀察到 `mouseover` 的觸發時機早於 `mouseenter` 。
### 小知識
- 與 `mouseleave` 事件相對應的還有 `mouseout` 事件，前者無事件冒泡；後者有事件冒泡。
## 了解更多
- [Kuro－那些你知道與不知道的事件們](https://ithelp.ithome.com.tw/articles/10192175)：本文最主要的參考範例。
- [sh1zuku－Mouse Event 小筆記](https://medium.com/@shizukuichi/mouse-event-%E5%B0%8F%E7%AD%86%E8%A8%98-feb5dd866b0)：了解更多滑鼠相關事件。