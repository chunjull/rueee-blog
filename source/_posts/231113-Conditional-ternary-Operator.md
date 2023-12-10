---
title: '#20 條件判斷：三元運算子'
category: DoJS
tags:
  - JavaScript
abbrlink: 4128159221
date: 2023-11-13 00:00:00
---
三元運算子也提供簡潔的條件判斷方式。
<!--more-->
## 快速了解
在 JS 的運算子種類中，存在一個用途跟 `if...else` 和 `switch` 很接近的運算子——三元運算子。
三元運算子，又稱「條件運算子」，是 JS 中唯一用到三個運算元的運算子，以「條件」、「問號」、「冒號」三個元素所組成。
在一個條件後面會跟著一個問號，如果條件是「truthy」，在冒號前的表達式會被執行；如果條件是「falsy」，在冒號後面的表達式會被執行。
```jsx
(條件) ? [數值/運算式 A] : [數值/運算式 B];
```

案例說明：判斷變數 `age` 是否大於或等於 18，若是，則 `status = "成人"` ；若不是，則 `status = "小孩"` 。
```jsx
var status = (age >= 18) ? "成人" : "小孩";
```
### 條件判斷整理
| 條件判斷方式 | 特色 | 範例 |
| --- | --- | --- |
|  `if...else`  | 推薦「入門學習者」使用 |  `if (5 > 2){console.log(”true”);} else { console.log(”false”);}`  |
|  `switch` | 推薦「複雜判斷」使用 |  `switch(){case1:…;}`   |
| 三元運算子 | 推薦「簡單判斷」使用 |  `max = (a > b)? a : b ;` |
### 小知識
- 三元運算子通常被用來當作 `if...else` 的簡潔寫法。
## 了解更多
- [MDN－三元運算子](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Conditional_operator)：了解三元運算子的常見用法。
- [ALPHACamp－流程控制 if/else 條件判斷](https://javascript.alphacamp.co/condition.html)：複習三種流程控制的條件判斷方式。
- [#16 邏輯運算子](https://chunjull.github.io/javascript/20231109/3042451770/)：回顧「falsy」和「truthy」的觀念。