---
title: '#103 物件導向'
category: DoJS
tags:
  - JavaScript
abbrlink: 2339315646
date: 2024-05-15 00:00:00
---
物件導向的程式設計在建立簡單模型後，可以快速建構一致的物件實體。
<!--more-->
## 快速了解
物件導向程式設計（Object-oriented programming）的基本概念為「採用物件（Objects）來模塑真實的實物世界」。
換句話說，我們可以在程式中透過操作「物件」（Objects）去塑造其模型，而物件能夠存放其相關資料與程式碼，並且能夠使用「方法」（Method）來進行存取。
大部分的物件導向程式語言是以「屬性為基礎」（class-based），但 JS 並沒有 `class` 與 `extends` ，卻能夠透過「原型」（prototype-based）建立物件之間的繼承關係。
因此，與其說 JS 是一門「物件導向」的程式語言，更準確地說，JS 應該是一門以「原型為基礎」的物件導向程式語言。
### 物件實體
過去，「物件」通常會被用來表達一組完整的概念，例如：一隻寶可夢的身高、體重、分類、性別、等屬性（class），且可以直接使用「物件實字」建立物件。然而，當我們需要建立一個龐大的寶可夢資料庫時，就會需要重複建立物件。
這時，如果導入物件導向的概念，先統一為「寶可夢」物件設定一個抽象化的簡單模型，再於程式中使用該模型來快速且有效地建構一致的物件實體（Object instance）。
從屬性（class）建立物件實體（Object instance）的過程即被稱為「實體化」（Instantiation）。
### 建構子函式
JS 會透過屬性（class）中的建構子函式（Constructor Function）來定義物件與功能。
使用建構子函式（Constructor Function）時，需要注意幾點：
1. 按照慣例，函式名稱會使用大寫開頭，以便一眼即可辨認該函式為建構子，例如： `Pokemon` 。
2. 建構子函式不能用 `return` 回傳其他內容，若加上 `return` 就只會回傳指定內容，而不會回傳一個新物件。
3. 呼叫建構子函式時，改成使用 `new` 運算子呼叫函式來建立物件。
```jsx
function Pokemon (name, height, weight, category, abilities) {
	this.name = name;
	this.height = height;
	this.weight = weight;
	this.category = category;
	this.abilities = abilities;
	console.log(this);
};

let Pikachu = new Pokemon('Pikachu', '0.4 m', '6.0 kg', 'Mouse', 'Static');
let Eevee = new Pokemon('Eevee', '0.3 m', '6.5 kg', 'Evolution', 'Runaway and Adaptability');
let Gengar = new Pokemon('Gengar', '1.5 m', '40.5 kg', 'Shadow', 'Cursed Body');

// Pokemon {name: 'Pikachu', height: '0.4 m', weight: '6.0 kg', category: 'Mouse', abilities: 'Static'}
// Pokemon {name: 'Eevee', height: '0.3 m', weight: '6.5 kg', category: 'Evolution', abilities: 'Runaway and Adaptability'}
// Pokemon {name: 'Gengar', height: '1.5 m', weight: '40.5 kg', category: 'Shadow', abilities: 'Cursed Body'}
```
以上述程式碼為例，先建立建構子函式 `Pokemon` 並設定一系列屬性（class），接著使用 `new` 運算子建立 `Pikachu` 、 `Eevee` 、 `Gengar` 這三個物件。使用 `new` 運算子時，首先會建立一個空物件，再執行 `Pokemon` 函式，最後將 `Pokemon` 函式中的 `this` 指定為剛剛的空物件。
因此，執行 `Pokemon()` 裡的 `this.name` 、 `this.height` 、 `this.weight` 、 `this.category` 、 `this.abilities` 等內容時，因為 `this` 指定的是空物件，所以參數傳入的屬性與方法，就會被放入該空物件中。
### 小知識
- 如果在建構子函式建立物件時沒有加上 `new` 運算子的話，該函式不會回傳任何東西，因此會得到 `undefined` 的結果。
- Constructor 又被翻譯為「建構式」、「建構器」。
## 了解更多
- [Kuro－深入理解 JavaScript 物件屬性](https://ithelp.ithome.com.tw/articles/10193747)：本文最主要的參考範例。
- [ALPHA Camp－JavaScript 物件導向](https://javascript.alphacamp.co/object-oriented.html)：了解「JS 物件導向為何」的系列文章。
- [MDN－建構子函數的使用](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Operators/new)：了解 `new` 運算子的意義。
- [#8 物件型別：物件](https://chunjull.github.io/javascript/20231101/3927311135/)：回顧物件的基本概念。