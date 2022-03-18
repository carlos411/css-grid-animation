# 7.2 AOS

## 官網

官網：[https://michalsnik.github.io/aos/](https://michalsnik.github.io/aos/)

說明文件：[https://github.com/michalsnik/aos](https://github.com/michalsnik/aos)

## 說明

在螢幕畫面中上下滑動頁面時，滑到指定位置，觸發動畫效果。

## 下載

![AOS CDN](../.gitbook/assets/aos\_cdn.png)

官方提供的初始化：

```markup
<script>
  AOS.init();
</script>
```

## 基本套用

### 範例 1：有哪些動畫效果

* data-aos：套用哪個動畫效果，[官方提供](https://github.com/michalsnik/aos#animations)。

在想要套用的元素上，加上 data-aos 屬性及動畫效果，例：

```markup
<div class="custom_block" data-aos="fade-up">測試的文字2</div>
```

最後再執行以下 JS 程式：

```javascript
AOS.init();
```

{% embed url="https://codepen.io/carlos411/pen/xxbLNzQ" %}



### 範例 2：瞭解 aos 基本屬性

* data-aos-easing：[官方提供](https://github.com/michalsnik/aos#easing-functions)。ease 是預設。
* data-aos-duration：0 \~ 3000 毫秒。400 是預設。
* data-aos-delay：0 \~ 3000 毫秒。0 是預設。
* data-aos-once：是否僅執行一次( true 或 false )。false 是預設。

藉由以下範例，自行測試上述四個屬性：

{% embed url="https://codepen.io/carlos411/pen/GRgvbqN" %}



### 範例 3：瞭解 data-aos-offset

* data-aos-offset：預設是 120，單位是px。當螢幕的下方經過該元素之後，這 120 指的是該元素的上方、螢幕的底部，距離是 120px 時，會觸發動畫效果。

以下範例請將 `data-aos-offset` 由 120 改為 0，觀察看看，也就是該元素的上方、螢幕的底部碰到的時候，就觸發動畫效果。

{% embed url="https://codepen.io/carlos411/pen/vYEjJLw" %}



### 範例 4：瞭解 data-aos-anchor-placement

* **`data-aos-anchor-placement`**：預設值是 **`top-bottom`**，第一個 top 指的是該元素的上方，第二個 bottom 指的是螢幕的下方。分別可以各自改成 `top`、`center`、`bottom` 的組合(例 `center-center` )，以達成該元素的哪個位置碰觸到螢幕的哪個位置時，觸發動畫效果。

以下例子 `data-aos-offset` 設定成 0，`data-aos-anchor-placement` 沿用預設值 `top-bottom` ，以便觀察：

{% embed url="https://codepen.io/carlos411/pen/OJPZjRV" %}

改成 **`top-center`**(該元素的上方、螢幕的中間)，然後自己做一個動畫效果的「觸發提示線」，以便觀察：

{% embed url="https://codepen.io/carlos411/pen/MWYGvjE" %}





### 範例 5：瞭解 data-aos-anchor

* **`data-aos-anchor`**：將該元素的觸發位置，改由另一個元素去決定觸發時機。

以下例子碰到黃色區域的時候，紅色元素的動畫效果就會觸發：

{% embed url="https://codepen.io/carlos411/pen/qBEYXqQ" %}





## 進階套用

### 範例 1：利用 AOS，套用自己寫的 animation

撰寫如下 css( 屬性 **data-aos** 等於 **rotate-animation** ，創造一個旋轉 360 度的動畫效果)，接下來直接在標籤加上 data-aos 屬性，然後再加上 **`rotate-animation`** 的值，就可以創造自訂的動畫效果了：

```css
[data-aos="rotate-animation"] {
  transform: rotate(0deg);
  transition: transform 1s;
}
[data-aos="rotate-animation"].aos-animate{
  transform: rotate(360deg);
}
```

觀察：在動畫效果觸發的時候，會自動加上 `aos-animate` 樣式。

{% embed url="https://codepen.io/carlos411/pen/RwNyZVb" %}

###

### 範例 2：寫一個 keyframes 的簡單動畫效果，讓 AOS 套用

撰寫如下 css( 屬性 **data-aos** 等於 **my-blink-animation** ，創造閃爍效果)，接下來直接在 data-aos 屬性上，加上 **`my-blink-animation`** 的值，就可以創造自訂的 keyframes 動畫效果了：

```css
@keyframes blink_animation {
  0%{
    opacity: 1;
  }
  25%{
    opacity: 0;
  }
  50%{
    opacity: 1;
  }
  75%{
    opacity: 0;
  }
  100%{
    opacity: 1;
  }
}
[data-aos="my-blink-animation"] {
}
[data-aos="my-blink-animation"].aos-animate{
  animation-name: blink_animation;
  animation-duration: 1s;
}
```

{% embed url="https://codepen.io/carlos411/pen/jOExLwm" %}

