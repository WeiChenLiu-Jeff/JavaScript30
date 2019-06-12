# 04 - Array Cardio Day 1

###### 怠慢許久，決定開始好好地把這些練習完成...
##### 這次主要是練習JS Array的操作，其中包含了`filter`、`map`、`sort`、`reduce`。

## Filter
#### 用途：
如同名稱所述，就是過濾陣列。
#### 範例：
```js
    const fifteen = inventors.filter(function (inventor) {
      if (inventor.year >= 1500 & inventor.year < 1600) {
        return true; // Keep it in the "fifteen array".
      }
    });
```
#### 說明：
先宣告一個空的陣列(`fiften`)準備放過濾出來的元素，使用方法`filter`，
裡面帶一個`function`(也可以用箭頭函式)去寫判斷式，回傳`true`者就會被放入先前宣告的陣列(`fiften`)

## Map
#### 用途：
依序對陣列每個元素處理、加工，並放到一個新的陣列。
#### 範例：
```js
const fullNames = inventors.map(inventor => 
                                inventor.first + ' ' + inventor.last); 
```
#### 說明：
先宣告一個空的陣列(`fullNames`)準備放處理過的元素，使用方法`map`，
裡面帶`function`去執行(範例是把`first`和`last`組合成一個字串)，
並不需要return就會放進新宣告的`fullNames`。

## Sort
#### 用途：
人如其名，就是排序。
#### 範例：
```js
    const alpha = people.sort((lastOne, nextOne) => {
      const [aLast, aFirst] = lastOne.split(', ');
      const [bLast, bFirst] = nextOne.split(', ');
      return aLast > bLast ? 1 : -1;
    });
```
#### 說明：
範例中先把姓名用`split`拆開，並且依照`Last`排序，
如果aLast>bLast的話就往後排，因次產生出來的陣列會是 **升冪排序**，
反之如果把後面的1、-1調換順序，就會變成 **降冪排序**。

## Reduce
#### 用途：
數值加總、統計運算、扁平化陣列。
#### 範例：
```js
    const totalYears = inventors.reduce((total, inventor) => {
      return total + (inventor.passed - inventor.year);
    }, 0); // 0為賦予total起始值
```
```js
    const data = ['car', 'car', 'truck',
                  'truck', 'bike', 'walk', 
                  'car', 'van', 'bike', 'walk', 
                  'car', 'van', 'car','truck'
                 ];
    const transportation = data.reduce((obj, item) => {
      if (!obj[item]) {
        obj[item] = 0;
      }
      obj[item]++;
      return obj;
    }, {})

```
#### 說明：
由於`reduce`比較複雜，所以放最後。

參數有兩個，第一個為return回來的值，第二個為陣列中下一個要帶入的值，
故使用`reduce`時，要給予一個預設值(因為第一次還沒東西return回來)。

第一個範例為單純的加總。

第二個範例為統計陣列中的詞彙共出現幾次，
陣列中預設值為空Object(`{}`)，
判斷式中每次都會判斷是否為新字詞，
如果是的話就創建一個`obj[item]`，然後+1並且return`obj`。

還有一個用途是 **扁平化陣列**
```js
var myArr = [
    [ 1, 2 ],
    [ 3, 4, 5 ],
    [ 6, 7, 8 ]
];

var newArr = myArr.reduce(function(arr, element) {
    return arr.concat(element);
}, []);

// [ 1, 2, 3, 4, 5, 6, 7, 8 ]
console.log(newArr);
```
