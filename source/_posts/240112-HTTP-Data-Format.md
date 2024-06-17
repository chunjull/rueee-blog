---
title: '#80 HTTP 資料格式'
category: DoJS
tags:
  - JavaScript
abbrlink: 3194480579
date: 2024-01-12 00:00:00
---
伺服器端會以 XML、JSON 等資料格式回應瀏覽器請求。
<!--more-->
## 快速了解
當瀏覽器發送請求時，伺服器端會以 XML、JSON 等資料格式回應。
### XML
XML（Extensible Markup Language），又稱為「可延伸標記式語言」。
和 HTML 一樣屬於標記語言（Markup Language），會使用「前後標籤」將內容包覆起來。
缺點是檔案較大、不易閱讀且處理較花時間，因此現代開發較少使用。
```xml
<cat>
	<name>Hello Kitty</name>
	<height>as five apples</height>
	<weight>as three apples</weight>
	<hobby>
		<sport>tennis</sport>
		<food>apple pie</food>
	</hobby>
</cat>
```
### JSON
JSON（JavaScript Object Notation），又稱為「JavaScript 物件表示法」。
格式容易理解，且相容性高，許多程式均支援讀取或修改，為現代最普遍、常用的資料格式。
JSON 會把所有的資料包在一個「物件」內傳遞，因此，撰寫時會使用一對大括號 `{}` 包住所有內容，欄位則由雙引號 `""` 包覆再由冒號 `:` 連接，每一項欄位則由逗號 `,` 隔開。
```json
{
	"name" : "Hello Kitty",
	"height" : "as five apples",
	"weight" : "as three apples",
	"hobby" : {
			"sport" : "tennis",
			"food" : "apple pie"
		}
}
```
使用 JSON 時需注意以下幾點：
1. 回傳值的型態是「字串」。
2. 支援許多資料格式：`[array]`、`{object}` 等；但值不能放函式。
3. JSON 格式字串不能使用註解。
## 了解更多
- [AWS－JSON 與 XML 之間有何區別？](https://aws.amazon.com/tw/compare/the-difference-between-json-xml/)：深入了解 XML 與 JSON 的差異。
- [Johnliutw－基本資料格式: XML + JSON](https://medium.com/johnliu-%E7%9A%84%E8%BB%9F%E9%AB%94%E5%B7%A5%E7%A8%8B%E6%80%9D%E7%B6%AD/%E5%BE%8C%E7%AB%AF%E5%B7%A5%E7%A8%8B%E5%B8%AB%E7%9A%84%E7%AC%AC%E4%B8%80%E5%A0%82%E8%AA%B2-7-%E5%9F%BA%E6%9C%AC%E8%B3%87%E6%96%99%E6%A0%BC%E5%BC%8F-xml-json-bf310696125)：了解更多 XML 與 JSON 的使用範例。
- [AppleBOY－你不可不知的 JSON 基本介紹](https://blog.wu-boy.com/2011/04/你不可不知的-json-基本介紹/)：深入了解 JSON 的使用方式。