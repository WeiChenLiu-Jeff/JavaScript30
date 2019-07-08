# 05 - Flex Panel Gallery

##### 這次主要練習到的有CSS屬性`flex`

`flex`是一個如其名很有彈性、方便地可以幫助版面元素排版的屬性。
<br>

### 操作步驟

首先需要先將你的元素加上這個屬性：

`display: flex;`

然後告訴它你的佈局：

`flex: 1 0 auto;`

這邊是個縮寫組合，
分別代表`flex-grow`、`flex-shrink`、`flex-basis`三個屬性。
詳見最下面的說明。

並且在元素上面加上監聽事件：
```js
    const panels = document.querySelectorAll('.panel');

    function toggleOpen() {
      this.classList.toggle('open');
    }

    function toggleActive(e) {
      if (e.propertyName.includes('flex')) {
        this.classList.toggle('open-active');
      }
    }

    panels.forEach(panel 
                   => panel.addEventListener('click', toggleOpen));
    panels.forEach(panel 
         => panel.addEventListener('transitionend', toggleActive));
```

當中`toggle`是開關的意思，意指重複操作可以添加或取消該class。
監聽事件中的`transitionend`則是監聽該元素CSS的`transition`並在完成後觸發。

***
#### flex-grow
代表將餘下的空間分配補滿，
假設全部元素設為1則每個元素都會分配到相同的餘額，
若設定不同數值則按照比例分配。

#### flex-shrink
容器縮小時，元素壓縮的比例分配，
若全部設定為0，則容器縮小時，元素會固定不動，
若全部設定為1(或相同數值)，則會以相同比例壓縮，
若只設定某元素有`flex-shrink`，則只會壓縮該元素。
_ps.壓縮是以元素的原始大小，_ _**依比例下降。**_

#### flex-basis
決定元素在容器內的初始大小。
***