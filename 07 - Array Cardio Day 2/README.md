# 07 - Array Cardio Day 2

##### `some`、`every`、`find`、`findIndex`

## some

判斷陣列中是否有 **部分** 元素符合條件

```js
    const isAdult = people.some(person => (new Date()).getFullYear() - person.year >= 19);
    console.log({
      isAdult
    });
```

創建一個變數`isAdult`，並且用`people.some`判斷回傳是否內含大於等於19歲的元素。

----

## every

判斷陣列中是否 **所有** 元素皆符合條件

```js
    const allAdults = people.every(person => (new Date()).getFullYear() - person.year >= 19);
    console.log({
      allAdults
    });
```
創建一個變數`allAdults`，並用`people.every`判斷回傳是否所有元素皆大於等於19歲。

---

## find

尋找出符合條件的 **元素**

```js
    const comment = comments.find(comment => comment.id === 823423);
    console.log(comment);
```

創建`comment`，並使用`comments.find`比對`id`等於`823423`的元素且回傳。

---

## findIndex
尋找出符合條件的 **元素位置**
```js
    const index = comments.findIndex(comment => comment.id === 823423);

    const newComments = [
      ...comments.slice(0, index),
      ...comments.slice(index + 1)
    ]
    console.table(newComments);
```

創建`index`，使用`comments.findIndex`找出符合條件的 **元素位置**，之後使用slice切出新的陣列(此題要求為刪除特定元素）。

---
## 展開運算子(spread)
補充說明，在 `findIndex` 的程式碼中，用到了``...``

簡單地說，它可以把函數中許多的參數或陣列中許多的元素組合成一個新的變數。

```js
    function spreadTest(color, size, ...other) {
      console.log(color, size, other);
    }
    spreadTest('Red', 256, 'iphone', '$100');
    // Red 256 ["iphone","$100"]
```
上述輸出結果為 `` Red 256 ["iphone","$100"] ``，可以看到原本`spreadTest`僅接受`color`和`size`變數傳入，但後面加了```...other```，可以使後面多的變數組合成一個新的陣列。



    