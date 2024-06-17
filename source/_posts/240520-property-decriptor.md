---
title: '#108 屬性描述器'
category: DoJS
tags:
  - JavaScript
abbrlink: 1683460589
date: 2024-05-20 00:00:00
---
使用屬性描述器，可以更方便地存取、修改物件屬性。
<!--more-->
## 快速了解
ES5 開始，JS 新增了一種名為「屬性描述器」（Property descriptor）的特殊屬性物件，可以透過新的物件模型來設定物件屬性的存取、刪除與列舉等功能。
### 六大分類
屬性描述器可分為六種：
- `value` ：屬性的值。
- `writable` ：定義屬性是否可以改變，若為 `false` 則是唯讀屬性。
- `enumerable` ：定義物件內的屬性是否可以透過 `for-in` 語法或 `Object.keys()` 來迭代列舉。
- `configurable` ：定義屬性是否可以刪除或修改屬性內的 `writable` 、 `enumerable` 及 `configurable` 設定。
- `get` ：物件屬性的 getter function。
- `set` ：物件屬性的 setter function。
除了 `value` 之外的值都可以不設定， `writable` 、 `enumerable` 及 `configurable` 的預設值是 `true` ， `get` 與 `set` 若無特別指定則是 `undefined` 。
### 設定方式
屬性描述器可以透過 `Object.create()` 在物件建立時就設定，還可以透過 ES5 提供的 `Object.defineProperty()` 來處理並搭配 `Object.getOwnPropertyDescriptor()` 檢查物件屬性描述器的狀態。
```jsx
const Pokemon = { };
Object.defineProperty(Pokemon, 'name', {
	value: 'Pikachu',
	writable: false,
	enumerable: false,
	configurable: false
});

Object.getOwnPropertyDescriptor(Pokemon, 'name');
```
 `Object.defineProperty()` 可以針對物件一次性設定多個屬性描述或分別設定。此外，若透過此方式建立物件屬性，不論 `writable` 、 `enumerable` 或 `configurable` ，其預設值都是 `false` 。
### 屬性的 get 與 set 方法
使用 `Object.defineProperty()` 語法，可以直覺地定義屬性的 `get` 與 `set` 方法，例如：
```jsx
const Pokemon = { };
Object.defineProperty(Pokemon, 'name',{
	get: function (){
		console.log('get');
		return this._name_;
	},
	set: function (name){
		console.log('set');
		this._name_ = name;
	}
});
```
以上述程式碼為例，我們可以分別為 `name` 屬性定義 `get` 與 `set` 方法，但實際上，是透過另一個屬性 `_name_` 來作為該 `name` 屬性的封裝。
要特別注意的是：若定義了 `get` 與 `set` 方法，就表示開發者要自行控制屬性的存取，故無法再去定義 `value` 或 `writable` 的屬性描述。
### 小知識
- 若在「嚴格模式」下，使用 `Object.defineProperty()` 設定屬性描述或刪除屬性，會發生 `TypeError` 的錯誤。
## 了解更多
- [Kuro－深入理解 JavaScript 物件屬性](https://ithelp.ithome.com.tw/articles/10193747)：本文最主要的參考範例。