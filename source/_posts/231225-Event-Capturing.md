---
title: '#62 事件捕獲'
category: DoJS
tags:
  - JavaScript
abbrlink: 2256329046
date: 2023-12-25 00:00:00
---
事件捕獲機制和「事件冒泡」相反，是由上到下觸發。
<!--more-->
## 快速了解
事件捕獲（Event Capturing）與「事件冒泡」機制相反，會「由上到下」傳遞。
### 事件捕獲範例
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
點擊 `<div>CLICK</div>` 元素後，在「事件捕獲」機制下，觸發事件的順序是：
1.  `document` 
2.  `<html>` 
3.  `<body>` 
4.  `<div>CLICK</div>` 
 `click` 事件由上到下依序被觸發。
## 了解更多
- [Kuro－事件機制的原理](https://ithelp.ithome.com.tw/articles/10191970)：本文最主要的參考範例。
- [Event Flow: capture, target and bubbling](http://www.java2s.com/Book/JavaScript/DOM/Event_Flow_capture_target_and_bubbling.htm)：事件捕獲示意圖。