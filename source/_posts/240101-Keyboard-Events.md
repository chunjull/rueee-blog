---
title: '#69 鍵盤相關事件'
category: DoJS
tags:
  - JavaScript
abbrlink: 2442920394
date: 2024-01-01 00:00:00
---
常見的鍵盤事件可分為「壓下」、「按住」、「放開」三種。
<!--more-->
## 快速了解
常見的鍵盤相關事件有以下三種，在多數情況下會將鍵盤事件註冊在 `input` 等表單輸入框上。
- `keydown` 事件：「壓下」鍵盤按鍵時會觸發 `keydown` 事件。
- `keypress` 事件：除了<kbd>Shift</kbd>、<kbd>Fn</kbd>、<kbd>CapsLock</kbd> 這三種按鍵外，其他按鍵被按住時會觸發，若按著不放則會連續觸發。
- `keyup` 事件：「放開」鍵盤按鍵時觸發。
### 事件執行順序
如果針對某元素同時綁定上述三個鍵盤事件，其執行順序會是：
```jsx
"keydown"
"keypress"
"keyup"
```
### 小知識
- 目前已不推薦使用下面推薦文章中的 `event.keyCode` 屬性，參見文章：[MDN－KeyboardEvent.keyCode](https://developer.mozilla.org/zh-CN/docs/Web/API/KeyboardEvent/keyCode#%E6%B5%8F%E8%A7%88%E5%99%A8%E5%85%BC%E5%AE%B9%E6%80%A7)。
## 了解更多
- [Kuro－那些你知道與不知道的事件們](https://ithelp.ithome.com.tw/articles/10192175)：本文最主要的參考範例。