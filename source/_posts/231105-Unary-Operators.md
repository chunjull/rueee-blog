---
title: "#12 算術運算子：一元運算子"
category: DoJS
tags:
  - JavaScript
abbrlink: 1630436862
date: 2023-11-05 00:00:00
---
一元運算子只需要單個數值就可以完成運算，有正號、負號、遞增、遞減四種。
<!--more-->
## 快速了解
算術運算子還有一種——只需要單個數值即可完成運算的「一元運算子」。
### 正號與負號
正號 `+` 與負號 `-` 分別代表數字的「正數」與「負數」的狀態。
- 當後面是數字時，結果會是該數值的正數或負數。
- 當後面是非數字的基本型別時，會先以 `Number()` 嘗試轉型，再由正、負號決定其數值。
- 當後面是物件型別時，會先以 `valueOf()` 取得數值，再由正、負號決定其數值。
- 若得到 `NaN`，結果就是 `NaN`。
### 遞加與遞減
「遞增」指變數遇上 `++` 就會加 1，也可以想成是 `a=a+1`；「遞減」指變數遇上 `--` 就會減 1，也可以想成是 `a=a-1`。
值得注意的是，這兩個運算子在變數的前、後，會產生不同的結果。當運算子在變數後面時，回傳結果會是「原始數值」；當運算子在變數前面時，回傳結果會是「+1 之後的結果」。但事後將結果印出時，回傳結果都會是「+1 之後的結果」。
```jsx
var a = 10;
var b = 10;
console.log(a++); // 10
console.log(++b); // 11
console.log(a); // 11
console.log(b); // 11
```
### 運算子整理
| 運算子 | 說明 | 範例 |
| --- | --- | --- |
| + | 一元正號運算子 | +8 |
| - | 一元負號運算子 | -x |
| ++ | 遞增運算子 | a++ |
| -- | 遞減運算子 | 5— |
### 小知識
- 加號和 `Number()` 有一樣的數字轉型效果。
## 了解更多
- [Kuro－「比較」與自動轉型的規則](https://ithelp.ithome.com.tw/articles/10191254)：本文最主要的參考範例。
- [MDN－一元正號運算子（+）](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Unary_plus)：觀看更多一元正號運算子的自動轉型範例。
- [MDN－一元負號運算子（-）](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Unary_negation)：觀看更多一元負號運算子的自動轉型範例。
- [MDN－遞增運算子（++）](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Increment)：觀看更多遞增運算子的範例。
- [MDN－遞減運算子（--）](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Decrement)：觀看更多遞減運算子的範例。