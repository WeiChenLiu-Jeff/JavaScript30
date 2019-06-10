# 01 - JavaScript Drum Kit
<br>

使用`<audio>`標籤放入`data-key`和`src`

```html
<audio data-key="65" src="sounds/clap.wav"></audio>
```
<br>


當鍵盤按下時會執行`playSound`
```js
window.addEventListener('keydown', playSound);
```
<br>

取得吻合KeyCode的`<audio>`標籤和`<div>`，準備操作他們
```js
const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
const key = document.querySelector(`.key[data-key="${e.keyCode}"]`);
```
<br>

將音訊檔的時間歸零，然後播放
```js
audio.currentTime = 0;
audio.play();
```
<br>

載入時會先將所有key加入這個EventListener，<br>CSS完成變化後，來移除CSS效果<br>(按下按鈕播放完後會觸發`removeTransition`)
```js
const keys = document.querySelectorAll('.key');
keys.forEach(key => key.addEventListener('transitionend',removeTransition));
```
```js
function removeTransition(e){
      if(e.propertyName !== 'transform') return;
      this.classList.remove('playing');
    }
```
