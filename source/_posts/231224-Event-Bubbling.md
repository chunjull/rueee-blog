---
title: '#61 事件冒泡'
category: DoJS
tags:
  - JavaScript
abbrlink: 1379383071
date: 2023-12-24 00:00:00
---
事件冒泡機制指「由啟動事件逐層向上依序被觸發」。
<!--more-->
## 快速了解
事件冒泡（Event Bubbling）指「從啟動事件的元素節點開始，逐層往上傳遞」，直到整個網頁的根節點—— `document` 為止。
### 事件冒泡範例
```html
<!DOCTYPE html>
<html>
<head>
	<title>TITLE</title>
</head>
<body>
	<div>CLICK</div>
</body>
</html>
```
點擊 `<div>CLICK</div>` 元素後，在「事件冒泡」機制下，觸發事件的順序是：
1.  `<div>CLICK</div>` 
2.  `<body>` 
3.  `<html>` 
4.  `document` 
由 `click` 事件逐層向上依序被觸發。
## 了解更多
- [Kuro－事件機制的原理](https://ithelp.ithome.com.tw/articles/10191970)：本文最主要的參考範例。
- [Event Flow: capture, target and bubbling](http://www.java2s.com/Book/JavaScript/DOM/Event_Flow_capture_target_and_bubbling.htm)：事件冒泡示意圖。