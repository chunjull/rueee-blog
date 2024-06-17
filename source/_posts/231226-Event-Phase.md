---
title: '#63 事件傳遞'
category: DoJS
tags:
  - JavaScript
abbrlink: 236790616
date: 2023-12-26 00:00:00
---
事件傳遞的基礎原則：先捕獲再冒泡。
<!--more-->
## 快速了解
事件流程有兩種機制，分別是「事件冒泡」與「事件捕獲」。
乍看之下，這兩種機制互不相關。但其實，事件會同時依賴這兩種機制，故兩者都會被執行。
### 事件傳遞機制
基本上，DOM 事件傳遞機制可分成三個階段：
1. 捕獲階段（Capturing Phase）
2. 傳遞到元素本身（Target Phase）
3. 冒泡階段（Bubbling Phase）
任何事件在傳遞時，都會按照這個順序進行：當觸發底層節點事件的同時，上層所有節點也會被觸發。
事件傳遞會遵守兩個原則：
1. 先捕獲，再冒泡。
2. 當事件傳到 `target` 本身，沒有分捕獲跟冒泡。
具體來說，觸發事件時會先進行「捕獲階段」，從最外層的根節點 `document` 開始往內傳遞到事件目標 `target` ；接著再進行「冒泡階段」，由下往上回傳。
## 了解更多
- [Kuro－事件機制的原理](https://ithelp.ithome.com.tw/articles/10191970)：本文最主要的參考範例。
- [itsems－Javascript 中的 DOM 事件傳遞機制：捕獲與冒泡](https://medium.com/itsems-frontend/javascript-event-bubbling-capturing-794cd2d01e61)：了解完整的事件傳遞過程。
- [Huli－DOM 的事件傳遞機制：捕獲與冒泡](https://blog.huli.tw/2017/08/27/dom-event-capture-and-propagation/)：深入了解事件傳遞過程。