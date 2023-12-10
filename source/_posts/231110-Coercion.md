---
title: '#17 自動轉型'
category: DoJS
tags:
  - JavaScript
abbrlink: 266130255
date: 2023-11-10 00:00:00
---
不同型別的資料在運算時，JS 會先「自動轉型」。
<!--more-->
### 基礎規則
- 如果其中一個是布林值，會將 `true` 轉為數字的 1， `false` 則變成數字的 0。
- 如果是字串與數字，會先透過 `Number()` 把字串轉為數字。
- 如果其中一個是「物件」型別，而另一方是基本型別時，會先透過物件的 `valueOf()` 方式取得對應的基本型別值。
### 複習賦值運算子
- `NaN` 不等於 `NaN` ，不論是在相等或全等的情況。
- 當兩個「物件」比較時，要看兩者是否指向同一個「實體」，只有在指向同一個「實體」時才會回傳 `true` 。
### 複習比較運算子
- 兩者都是數字時，單純就其字面大小比較。
- 如果其中一個是數字，另一方不是，則會先將另一方轉為數字再比較。
- 如果兩者都是字串，則會依照字母順序比較。
- 如果其中一個是布林值，會將 `true` 轉為數字的 1， `false` 則變成數字的 0。
- 如果其中一個是「物件」型別，而另一方是基本型別時，會先透過物件的 `valueOf()` 方式取得對應的基本型別值。
### 小知識
- 字母順序依照的規則為字典序（standard lexicographical ordering），要注意大小寫字母的順序並不同。
## 了解更多
- [Kuro－Boolean 的真假判斷](https://ithelp.ithome.com.tw/articles/10191343)：本文最主要的參考範例。
- [Summer－強制轉型](https://www.cythilya.tw/2018/10/15/coercion/)：了解詳細的 JS 轉型規則。
- [Genos－強制轉型及轉換技巧](https://genos.coderbridge.io/2021/11/18/coercion/)：回顧 JS 的轉型規則。
- [Oh-My-Dear-JavaScript](https://www.thomas-yang.me/projects/oh-my-dear-js/)：觀看 JS 真值表。