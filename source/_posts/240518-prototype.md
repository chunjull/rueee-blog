---
title: '#106 原型鍊與繼承'
category: DoJS
tags:
  - JavaScript
abbrlink: 158954928
date: 2024-05-18 00:00:00
---
原型繼承的目的是「讓一個物件取得另一個物件的屬性與方法」。
<!--more-->
## 快速了解
JS 是一種基於「原型」的物件導向程式語言，其繼承方法是透過「原型」（prototype）進行實作。藉由「原型」繼承，可以讓本來沒有某個屬性的物件去存取其他物件的屬性，而該「被繼承的物件」就被稱為「原型」。
需要特別注意的是：在原型繼承的規則裡，同一個物件無法指定兩種原型物件。但這點在「原型鏈」（Prototype Chain）中可以得到解決。
### 原型物件
嘗試對某個物件存取一個不存在該物件的屬性時，瀏覽器會繼續往「原型物件」（ `[[prototype]]` ）尋找，順著原型鏈找到最頂層的 `object.prototype` 才會停止，該物件即是 JS 所有物件的起源。
因此， `object.prototype` 提供的所有方法，JS 中的任何物件都可以呼叫它，例如： `obejct.prototype.hasOwnProperty()` 、 `object.prototype.toString()` 、 `object.prototype.valueOf()` 等方法。即便建立物件時，沒有定義上述方法，但基於原型鏈繼承的原則，仍然可以呼叫這些方法。
### 建構子與原型
在每一個函式被建立時，都會有原型物件，當開發者把該函式當作建構子來建立新物件時，該函式的原型物件會被當作這個新物件的原型。
```jsx
var Pokemon = function (){};
Pokemon.prototype.saySomething = function (){
	return "Pika-pika!";
};
var p1 = Pokemon();
var p2 = new Pokemon();
p1.saySomething();  // undefined
p2.saySomething(); // "Pika-pika!"
```
以上述程式碼為例，變數 `p1` 是直接呼叫 `Pokemon` 的結果，但因為該函式沒有回傳，結果會是 `undefined` 。變數 `p2` 則是透過 `new` 運算子來建立物件，但由於函式也是物件，所以可以透過原型 `prototype` 進而擴充每一個透過該函式所建構的物件。因此，透過 `new Pokemon()` 建立新物件並指定給變數 `p2` 後，即使尚未對該變數定義 `saySomething()` 方法，仍可以使 `p2` 透過原型取得呼叫 `saySomething()` 的能力，並回傳 `“Pika”` 的結果。
然而，如果在建構子中建立「同名」的實例方法，則會優先存取自己的屬性或方法，如果沒有才會再順著原型鏈向上尋找，這點需要特別注意。
### 原型與繼承
當函式被建立時，都會擁有原型物件 `prototype` 。藉由擴充該 `prototype` 物件，能夠讓每一個透過此函式建構的物件都有該「屬性」或「方法」。
```jsx
const Pokemon = function (name) {
	this.name = name;
};
Pokemon.prototype.saySomething = function (){
	return this.name + " says: pika!";
};
var p = new Pokemon("Pikachu");
p.saySomething(); // Pikachu says: pika!
```
以上述程式碼為例，使用 `new` 運算子建構一個 `Pokemon` 的實體——即物件 `p` 時，該物件 `p` 的原型物件會自動指向建構子的 `prototype` 屬性，也就是 `Pokemon.prototype` 。
此外，也可以透過原型新增「方法」（method），此方式在原型新增後即可馬上使用：
```jsx
const Pokemon = function (name) {
	this.name = name;
};
var p = new Pokemon("Eevee");
p.attack(); // Uncaught TypeError: p.attack is not a function
Pokemon.prototype.attack = function (){
	return "Bite!";
};
p.attack(); // "Bite!"
```
在上述程式碼中，原本物件 `p` 與其原型鏈上的所有物件都沒有 `attack()` 方法，在透過 `Pokemon.prototype.attack` 新增對應方法後，無需再重新設置物件 `p` ，而是立刻就可以使用 `p.attack()` 來呼叫。
### 原型繼承方式
可以將「原型繼承的屬性或方法」統整成以下情況：
- 如果物件實體與它的原型同時用有同樣的屬性或方法時，會**優先存取自己的屬性或方法**。
- 如果物件實體找不到某個屬性或方法時，會往它的原型物件尋找。
  1. 若在原型物件或更上層的原型物件有發現這個屬性，且屬性描述的 `writable` 為 `true` ，則會為該物件實體新增對應的屬性或方法。
  2. 同上，但若該屬性描述的 `writable` 為 `false` ，則等於目標物件會多出一個「唯讀」屬性，且事後無法再新增或修改。
  3. 若在原型物件或更上層的原型物件有發現某屬性，但該屬性是一個「設值器」（setter function），則呼叫對象會是該設值器，目標物件的屬性也無法被重新定義。
### 檢查屬性
原型有兩種檢查方式，一種是透過「原型鏈」檢查屬性；另一種則是檢查某屬性是否為「物件本身」所有。
- 第一種透過「原型鏈」檢查屬性的方式，可以使用 `in` 運算子：

```jsx
var Pokemon = function (){};
Pokemon.prototype.saySomething = function (){
	return "Pika!";
};
var p2 = new Pokemon();
console.log('saySomething' in p2); // true
```
- 第二種檢查則可以透過 `hasOwnProperty()` 方法進行：

```jsx
var Eevee = { bite: true };
var Flareon = { flamethrower: true };
var Vaporeon = { waterGun: true };
console.log(Eevee.hasOwnProperty('bite')); // true
console.log(Eevee.hasOwnProperty('flamethrower')); // false
```
### 特殊屬性：__proto__
大多數瀏覽器的 JS 引擎都有提供一種名為 `__proto__` 的特殊屬性，其目的為讓開發者能夠取得某物件的原型物件。但並非所有 JS 執行環境都支援該屬性。
好消息是：從 ES5 開始，可以透過標準方法 `Object.getPrototypeOf()` 來取得某物件的原型物件。因此，不論是透過特殊屬性或標準方法的方式，都可以取得目標物件的原型物件 `[[prototype]]` 。
此外，如果要透過「物件」來達到原型繼承的話，則可以使用下列方式：
1.  `Obejct.setPrototypeOf()` ：將特定物件指定為目標物件的「原型」。
2.  `Object.create()` ：先建立一個作為「原型」的物件，在透過此方法產生新物件。
## 了解更多
- [Kuro－ ****物件與原型鏈](https://ithelp.ithome.com.tw/articles/10194154)：本文最主要的參考範例。
- [ALPHACamp－原型繼承與原型鏈](https://javascript.alphacamp.co/prototype-prototype-chain.html)：了解原型繼承與原型鏈的意義。