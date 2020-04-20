# 06 - Type Ahead

##### 這次主要練習是fetch、blob

```js
const endpoint = 'https://gist.githubusercontent.com/Miserlou/c5cd8364bf9b2420bb29/raw/2bf258763cdddd704f8ffd3ea9a3e81d25e2c6f6/cities.json';
    let cities = [];
    fetch(endpoint)
      .then(blob => blob.json())
      .then(data => cities.push(...data));
```
---
#### Fetch
##### fetch主要是去endpoint取得json回來，
- ##### fetch傳回來的是ES6的Promise
- ##### `.then()`是下一步(成功取得後執行什麼)
- ##### `.catch()`是取得失敗要執行的
---
#### Blob
>Blob（Binary Large Object）物件代表了一個相當於檔案（原始資料）的不可變物件。Blob 中的資料並不一定是 JavaScript 原生的格式。File 介面基於 Blob，繼承 blob 並擴充其功能以支援操作使用者系統上的檔案。

也可以處理圖片檔案之類的。

---

#### Literal template、正則式
此題還有用到這兩項，先透過正則式篩選出符合得項目，並提取字串，再生成`Literal template` `replace`掉原本的HTML。