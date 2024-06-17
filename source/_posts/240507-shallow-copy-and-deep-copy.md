---
title: '#95 淺拷貝與深拷貝'
category: DoJS
tags:
  - JavaScript
abbrlink: 124095393
date: 2024-05-07 00:00:00
---
淺拷貝會共用同一個記憶體空間；深拷貝則使用兩個不同的記憶體空間。
<!--more-->
## 快速了解
JS 資料型別分為兩大類：基本型別與物件型別。
兩者最大的差異在於：
- 基本型別使用 Pass by value 的方式傳遞參數，複製變數時會直接複製「值」（value）。會將「值」真實地複製一份，因此不會互相影響到最終結果。
- 物件型別則使用。Pass by reference 的方式傳遞參數，複製變數時則會複製「址」（address）。複製出來的「值」與原本的變數之間會互相影響。
物件型別這種「複製的址會和原始變數共用同一記憶體空間」的複製方法，被稱為「淺拷貝」（Shallow Copy）；而透過特定方法，使「複製的址和原始變數使用不同記憶體空間」的方法，則被稱為「深拷貝」（Deep Copy）。
### 淺拷貝
淺拷貝只拷貝「物件或陣列中的第一層資料」，第二層以上的資料不會真的拷貝，而是會參考到和原本相同的物件或陣列實體，因此會互相影響。
常見的 JS 拷貝工具都是淺拷貝，例如：使用其餘運算子 `…` 、使用內建方法 `Object.assign()` 等。
```jsx
let a = {x:3, y:4, data:[1,2,3]};
let b = {...a};
b.data[0] = 4;
console.log(a.data[0]); // 4
```
在上述程式碼中， `data` 中的陣列沒有真的被拷貝，a 和 b 物件中的 `data` 仍參考到同一個陣列實體。b 對 `data` 的操作影響到 a 的 `data` ，使最終印出結果是 `4` 。
### 深拷貝
深拷貝會「完全拷貝物件底下所有層次的資料」，建立兩個完全獨立的物件實體，且互相不影響。
```jsx
let a = {x:3, y:4, data:[1,2,3]};
let str = JSON.stringify(a);
let b = JSON.parse(str);
b.data[0] = 4;
console.log(a.data[0]); // 1
```
在上述程式碼中，先使用 `JSON.stringify()` 將物件字串化（Serialize），並使用 `JSON.parse()` 根據字串化的資料重新建立物件結構，完成深拷貝。經過深拷貝後，兩個物件完全獨立、不互相影響，變數 `b` 對 `data` 的操作**不會影響**到變數 `a` 的 `data` ，因此最終印出結果是 `1` 。
### 小知識
- 物件或陣列中，還包含其他的物件或陣列，才會產生「層次」。
## 了解更多
- [Andy Chen－關於JS中的淺拷貝(shallow copy)以及深拷貝(deep copy)](https://medium.com/andy-blog/%E9%97%9C%E6%96%BCjs%E4%B8%AD%E7%9A%84%E6%B7%BA%E6%8B%B7%E8%B2%9D-shallow-copy-%E4%BB%A5%E5%8F%8A%E6%B7%B1%E6%8B%B7%E8%B2%9D-deep-copy-5f5bbe96c122)：了解淺拷貝、深拷貝的差異。
- [城市碼農－JS 中的淺拷貝 (Shallow copy) 與深拷貝 (Deep copy) 原理與實作](https://www.programfarmer.com/articles/2021/javascript-shallow-copy-deep-copy)：透過案例了解拷貝方式的差異。
- [彭彭－JavaScript 物件的淺拷貝、深拷貝](https://youtu.be/tnT-XbrOKA0?si=6iGsC3lNtWWwIu5X)：了解淺拷貝、深拷貝的差異。