# 2.3 Grid 排版 - Items

Grid Items 相關屬性。

## grid-column

* 數值指的是 Grid Column Line 的意思。
* span 2：指的是擴展兩個欄的意思。

```css
/* 寫法一 */
grid-column: 1 / 3;

/* 寫法二：使用 line 的命名 */
/*
使用 Grid Line 的名稱，假設在 Grid Container 有設定：
grid-template-columns: [a] auto [b] auto [c] auto [d];
*/
grid-column: a / c;

/* 寫法三 */
grid-column-start: 1;
grid-column-end: 3;

/* 寫法四 */
grid-column: 1 / span 2;
```



例：

{% embed url="https://codepen.io/carlos411/pen/eYdMEwm" %}



## grid-row

* 數值指的是 Grid Row Line 的意思。
* span 2：指的是擴展兩個欄的意思。

```css
/* 寫法一 */
grid-row: 1 / 4;

/* 寫法二：使用 line 的命名 */
/*
使用 Grid Line 的名稱，假設在 Grid Container 有設定：
grid-template-rows: [a] auto [b] auto [c] auto [d];
*/
grid-row: a / d;

/* 寫法三 */
grid-row-start: 1;
grid-row-end: 4;

/* 寫法四 */
grid-row: 1 / span 3;
```



例：

{% embed url="https://codepen.io/carlos411/pen/poELWzM" %}



## grid-area

原來九個欄位如下：

![](../.gitbook/assets/grid\_original\_nine.png)

將 4 的那個欄位，擴展到 4、5、7、8，變成如下：

![](../.gitbook/assets/grid\_area\_sample.png)

```css
/* 寫法一 */
grid-row-start: 2;
grid-column-start: 1;
  
grid-row-end: 4;
grid-column-end: 3;

/* 寫法二 */
grid-area: 2 / 1 / 4 / 3;

/* 寫法三 */
grid-area: 2 / 1 / span 2 / span  2;
```



例 1：使用 Grid Line 來設定範圍：

{% embed url="https://codepen.io/carlos411/pen/JjRLroE" %}



例 2：使用 grid-area 來將欄位指定位置(例：將 1 和 9 對調)：

{% embed url="https://codepen.io/carlos411/pen/OJRvxbr" %}



例 3： **`grid-area`** 也可以用來設定這個 Item 的**名稱**，然後就可以在 `Grid Container` 中使用 **`grid-template-areas`** 中直接指定名稱。

```css
div.item{
  grid-area: header;
}
```

{% hint style="info" %}
範例請參考 **`grid-template-areas`** 屬性。
{% endhint %}



## 排列相關



### justify-self

請參考 `justify-items`。



### align-self

請參考 `align-items`。



### place-self

請參考 `place-items`。

是 `justify-self` 和 `align-self` 的簡寫形式，格式如下：

```css
place-self: <align-self> <justify-self>;
```



## 練習

建立 `grid_practice.html` 來練習，請貼上以下原始碼：

{% tabs %}
{% tab title="HTML" %}
```markup
<div class="grid_container">
  <header class="grid_item">
    這是 header
  </header>
  <aside class="grid_item">
    這是 aside
  </aside>
  <main class="grid_item">
    這是 main
  </main>
  <section class="grid_item">
    這是 section
  </section>
  <footer class="grid_item">
    這是 footer
  </footer>
</div>
```
{% endtab %}

{% tab title="CSS" %}
```css
div.grid_container{
  border: 1px solid red;
  padding: 10px;
  display: grid;
  gap: 10px;
  grid-template-columns: 1fr 2fr 1fr;
}
div.grid_container .grid_item{
  border: 1px solid blue;
}
```
{% endtab %}
{% endtabs %}



使用 Grid 排版模式，變成如下圖佈局：

![](../.gitbook/assets/grid\_layout\_practice.png)



### 方式一：使用 Grid Line 來切

例如 `header.grid_item`：

```css
div.grid_container header.grid_item{
  grid-column: 1 / 3;
}
```



參考作法：

{% embed url="https://codepen.io/carlos411/pen/XWpMqYY" %}





### 方式二：使用命名方式

給定各個 Item 命名如下：

```css
div.grid_container header.grid_item{
  grid-area: header;
}
div.grid_container aside.grid_item{
  grid-area: aside;
}
div.grid_container main.grid_item{
  grid-area: main;
}
div.grid_container section.grid_item{
  grid-area: section;
}
div.grid_container footer.grid_item{
  grid-area: footer;
}
```



參考作法：

{% embed url="https://codepen.io/carlos411/pen/qBaMrmM" %}



