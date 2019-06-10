# 02 - JS + CSS Clock
<br>

這個時鐘主要是透過JS取得時間，並計算角度，

再控制CSS的`transform`，達到指針移動的效果．
<br>

一樣先用`querySelector`取得三根指針
```js
const secondHand = document.querySelector('.second-hand');
const minHand = document.querySelector('.min-hand');
const hourHand = document.querySelector('.hour-hand');
```
<br>

`setInterval()`可以定期去執行function`setDate`，後面參數放毫秒
```js
setInterval(setDate, 1000);
```
<br>


`setData`function裡面分別設定秒．分．時

下面只舉一個例子：<br><br>


先透過`new Date()`產生現在時間，

再用`getSeconds()`取得秒數，

算出角度之後直接透過JS去改變物件的Style

```js
const now = new Date();

const seconds = now.getSeconds();
const secondsDegrees = ((seconds / 60) * 360) + 90;
secondHand.style.transform = `rotate(${secondsDegrees}deg)`
```
