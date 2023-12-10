---
title: '#11 算術運算子：四則運算'
category: DoJS
tags:
  - JavaScript
abbrlink: 3439418316
date: 2023-11-04 00:00:00
---
算術運算子除了能夠進行四則運算，還影響著型別間的自動轉型問題。
<!--more-->
## 快速了解
算術運算子包括數學四則運算的加、減、乘、除和取餘數。
運算式會遵守「由左至右」且「先乘除後加減」的模式進行運算，需要時可加上小括號 `()` 輔助。
### 加號
加法運算子以加號 `+` 表示。
- 當前後兩者都是數字時，計算結果是兩個數值的和。
- 當其中一個是 `NaN` 時，結果必定也是 `NaN`。
- `Infinity` 與 `-Infinity` 的情況：
    - `Infinity` 與 `Infinity` 相加，結果是 `Infinity` 。
    - `-Infinity` 與 `-Infinity` 相加，結果是 `-Infinity` 。
    - `Infinity` 與 `-Infinity` 相加，結果是 `NaN`。
- 當其中一個不是數字時，會觸發自動轉型。
    - 若其中一個是字串，另一端會變「自動轉型」為字串後，連接在一起。
    - 當另一端是數字、布林值、物件時，會以 `.toString()` 轉型。
    - 當另一端是 `null`、`undefined` 時，會以 `String()` 將它們轉成 `“null”` 與 `“undefined”` 。
### 減號
減法運算子以減號 `-` 表示。
- 當前後兩者都是數字時，計算結果是兩個數值的差。
- 當其中一個是 `NaN` 時，結果必定也是 `NaN`。
- `Infinity` 與 `-Infinity` 的情況：
    - `Infinity` 與 `Infinity` 相減，結果是 `NaN`。
    - `-Infinity` 與 `-Infinity` 相減，結果是 `NaN`。
    - `-Infinity` 與 `Infinity` 相減，結果是 `-Infinity` 。
    - `Infinity` 與 `-Infinity` 相減，結果是 `Infinity` 。
- 當其中一個不是數字時，會觸發自動轉型。
    - 若其中一個是非數字的基本型別時，會以 `Number()` 嘗試轉為數字。
    - 若其中一個是物件型別時，會先以 `valueOf()` 取得數值再計算；若物件沒有 `valueOf()` 方法的話，則會先透過 `toString()` 轉成字串，再以 `Number()` 後的數字進行運算。
### 乘號
乘法運算子以星號 `*` 表示。
- 當前後兩者都是數字時，計算結果是兩個數值的乘積。
- 若計算結果超出數字範圍，會依結果是正數或負數決定是 `Infinity` 或 `-Infinity`。
- 當其中一個是 `NaN` 時，結果必定也是 `NaN`。
- 若其中一個不是數字時，JS 會先嘗試以 `Number()` 進行轉型再運算。
```jsx
1 * 5; // 5
10 * "10"; // 100
100 * "abc"; // NaN
1000 * NaN; // NaN
```
### 除號
除法運算子以斜線 `/` 表示。
- 當前後兩者都是數字時，計算結果是兩個數值的商。
- 當其中一個是 `NaN` 時，結果必定也是 `NaN`。
- 若其中一個不是數字時，JS 會先嘗試以 `Number()` 進行轉型再運算。
- 在被除數為 0 時，有三種情況：
    - 除數為正數，結果為 `Infinity`。
    - 除數為負數，結果為 `-Infinity`。
    - 除數為 0，結果為 `NaN`。
### 取餘數
取餘數運算子以百分比符號 `%` 表示。
- 當前後兩者都是數字時，計算結果是除法運算後的「餘數」。
- 當被除數是 `Infinity` 或 `-Infinity` 時，取餘數結果會是 `NaN`。
- 當被除數是一般數值，而除數為 `Infinity` 時，結果為被除數。
- 當被除數是一般數值，而除數為 0 時，結果為 `NaN`。
- 當其中一個是 `NaN` 時，結果必定也是 `NaN`。
- 若其中一個不是數字時，JS 會先嘗試以 `Number()` 進行轉型再運算。
### 運算子整理
| 運算子 | 說明 | 範例 |
| --- | --- | --- |
| + | 加法 | `10 + ”hello”` |
| - | 減法 | `100 - false` |
| * | 乘法 | `100 * 5` |
| / | 除法 | `20 / 2` |
| % | 取餘數 | `100 % 33` |
### 小知識
- 算術運算子還有一種：指數運算子，以雙星號 `**` 表示，用來計算以 a 為底的 b 次方。
## 了解更多
- [Kuro－運算式與運算子](https://ithelp.ithome.com.tw/articles/10191180)：本文最主要的參考範例。
- [MDN－加法運算子（+）](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Addition)：觀看更多加法運算子的自動轉型範例。
- [MDN－減法運算子（-）](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/Subtraction)：觀看更多減法運算子的自動轉型範例。
- [Genos－強制轉型及轉換技巧](https://genos.coderbridge.io/2021/11/18/coercion/)：預習 JS 的轉型規則。