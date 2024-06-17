---
title: '#60 事件流程'
category: DoJS
tags:
  - JavaScript
abbrlink: 2664330907
date: 2023-12-23 00:00:00
---
事件流程就是網頁元素接收事件的順序。
<!--more-->
## 快速了解
事件流程（Event Flow）指「網頁元素接收事件的順序」。
事件流程可以區分成兩種機制：
- 事件冒泡（Event Bubbling）。
- 事件捕獲（Event Capturing）。
### 事件流程範例
假設有兩個重疊的 `div` 元素，外層是 `<div id=”outer”>` ，而內層是 `<div id="inner">` ：
```html
<div id="outer">
	<div id="inner"></div>
</div>
```
在不考慮 `position: absolute;` 的前提下，內層一定在外層裡面，換言之， `inner` 是 `outer` 的一部份。因此，當我們點擊 `inner` 時，是否也代表我們也點擊到 `outer` ，甚至，代表我們實際上也點擊到整個網頁。
這樣「事件先後發生的網頁元素接收事件順序」，就是事件流程。
## 了解更多
- [Kuro－事件機制的原理](https://ithelp.ithome.com.tw/articles/10191970)：本文最主要的參考範例。