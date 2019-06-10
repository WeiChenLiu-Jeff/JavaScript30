# 03 - Playing with CSS Variables and JS
<br>

這篇主要是在說如何透過JS取得HTML的`value`、`dataset`
去控制CSS變數。
<br>

CSS變數使用方式：
```css
:root {
  --base: #ffc600;
  --spacing: 10px;
  --blur: 10px;
}

img {
  padding: var(--spacing);
  background: var(--base);
  filter: blur(var(--blur));
}

.hl {
  color: var(--base);
}
```
<br>

先取得所有`.controls input`的元素。
```js
const inputs = document.querySelectorAll('.controls input');
```
<br>

幫它們加入監聽事件，input改變或是滑鼠移動時，觸發`handleUpdate`。
```js
inputs.forEach(input => input.addEventListener('change', handleUpdate));
inputs.forEach(input => input.addEventListener('mousemove', handleUpdate));
```
<br>

透過`this.dataset.sizing`可以取得HTML tag上的`data-sizing`，同理也可以自行設定其他參數。

再透過`setProperty`去改變CSS的變數。
```html
<input id="spacing" type="range" name="spacing" min="10" max="200" value="10" data-sizing="px">
```
```js
function handleUpdate() {
  const suffix = this.dataset.sizing || '';
  document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
}
```