# 2.2 Grid 排版 - Container

## Container 相關屬性 - 1



### grid-template-columns 設定各欄寬度



設定 3 欄，每欄寬度自動分佈：

```css
grid-template-columns: auto auto auto;
```

設定 2 欄，第一欄寬度是 100px，第二欄寬度是 150px：

```css
grid-template-columns: 100px 150px;
```



例：

{% embed url="https://codepen.io/carlos411/pen/bGgewoj" %}



### grid-template-rows 設定各列高度



設定第一列的高度為 100px，第二列的高度為 150px：(註：大部份情況，高度應由內容來撐)

```css
grid-template-rows: 100px 150px;
```



例：

{% embed url="https://codepen.io/carlos411/pen/WNRxGzL" %}



### grid-auto-flow 設定流向

{% hint style="info" %}
需先瞭解 `grid-column` 及 `grid-row`，才能瞭解 `dense` 部份。
{% endhint %}



* `row`：預設值，設定 Items 沿著 row 的方向依序出現。
* `column`：設定 Items 沿著 column 的方向依序出現。
* `row dense`：加上 dense 會讓 Items 遞補。
* `column dense`：加上 dense 會讓 Items 遞補。



例：

{% embed url="https://codepen.io/carlos411/pen/xxgOEJE" %}





### grid-auto-rows 設定各列預設高度

各列高度由 `grid-template-rows` 來設定，

**其它列沒有指定到高度的**，如下範例，第一個列設定 200px，下一個列設定 300px，再下一列會是 200px，以此類推：

```css
grid-auto-rows: 200px 300px;
```



例：

{% embed url="https://codepen.io/carlos411/pen/NWdrRJJ" %}



### grid-auto-columns 設定各欄預設寬度

各欄寬度由 `grid-template-columns` 來設定，

**其它欄沒有指定到寬度的**，如下範圍，第一個欄設定 120px，下一個欄設定 180px，再下一欄會是 120px，以此類推：

```css
grid-auto-columns: 120px 180px;
```



例：

{% embed url="https://codepen.io/carlos411/pen/rNjLMgx" %}



## Container 相關屬性 - 2

### grid-template-areas 排版

{% hint style="info" %}
需先瞭解 `grid-area`，才能瞭解 `grid-template-areas` 部份。
{% endhint %}

用途：

1. 在 Grid Items 使用 **`grid-area`** 來設定各個 Item 的名稱。
2. 然後就可以在 Grid Container 中使用 **`grid-template-areas`** 來做排版。



`grid-template-areas` 的語法：

* 以雙引號(單引號也可)當做是一個列，然後如果要表達下一個列，那就再使用雙引號，各列的雙引號以空格做區隔。
* 有一個符號是 **`.`**，代表的意思是沒有名稱的 Grid Item。

例 1：

{% embed url="https://codepen.io/carlos411/pen/WNRxpqW" %}



### grid-template 簡寫形式

例1：

```css
grid-template-columns: auto auto auto;
grid-template-rows: 100px 150px;
/* 等同於 */
grid-template: 100px 150px / auto auto auto;
```



例2：

```css
grid-template-areas: "header header header" "aside main section" "aside footer footer";
/* 等同於 */
grid-template: "header header header" "aside main section" "aside footer footer";
```

{% embed url="https://codepen.io/carlos411/pen/abpZWwy" %}





### grid 簡寫形式

```css
grid-template-columns: auto auto auto;
grid-template-rows: 100px 150px;
/* 等同於 */
grid-template: 100px 150px / auto auto auto;
/* 等同於 */
grid: 100px 150px / auto auto auto;
```

```css
grid-template-areas: "header header header" "aside main section" "aside footer footer";
/* 等同於 */
grid-template: "header header header" "aside main section" "aside footer footer";
/* 等同於 */
grid: "header header header" "aside main section" "aside footer footer";
```

```css
grid: auto-flow 100px / 1fr 100px;
/* 等同於 */
grid-template-columns: 1fr 100px;
grid-auto-flow: row;
grid-auto-rows: 100px;


grid: auto-flow dense 100px / 1fr 100px;
/* 等同於 */
grid-template-columns: 1fr 100px;
grid-auto-flow: row dense;
grid-auto-rows: 100px;
```

```css
grid: 100px 300px / auto-flow 100px;
/* 等同於 */
grid-template-rows: 100px 300px;
grid-auto-flow: column;
grid-auto-columns: 100px;


grid: 100px 300px / auto-flow dense 100px;
/* 等同於 */
grid-template-rows: 100px 300px;
grid-auto-flow: column dense;
grid-auto-columns: 100px;
```



例：

```css
grid-template-rows: 100px 200px 300px;
grid-template-columns: auto auto auto;
grid-template-areas: "header header header" "aside main section" "aside footer footer";
/* 等同於 */
grid: "header header header" 100px "aside main section" 200px "aside footer footer" 300px / auto auto auto;
```

{% embed url="https://codepen.io/carlos411/pen/LYxZyrr" %}



### repeat() 與 minmax() 函式與 fr 單位



第一個參數：表示「第二個參數的內容」，要重覆幾次。例：

```css
grid-template-columns: repeat(3, 100px);
/* 等同於 */
grid-template-columns: 100px 100px 100px;
```

第一欄的寬度是 100px \~ 200px，例：

```css
/*
  三欄
  第一欄的寬度是 100px ~ 200px；
  第二欄的寬度是 100px；
  第三欄的寬度是 100px。
*/
grid-template-columns: minmax(100px, 200px) 100px 100px;
```



**`fr`** 是 fraction of the free space，也就是剩餘空間，以比例方式來分配，例：

```css
/*
  三欄：
  第一欄的寬度是 剩餘空間的 3/4；
  第二欄的寬度是 100px；
  第三欄的寬度是 剩餘空間的 1/4。
*/
grid-template-columns: 3fr 100px 1fr;
```

{% embed url="https://codepen.io/carlos411/pen/WNoBWML" %}



## Container 相關屬性 - 3



### column-gap 設定各欄間距

```css
column-gap: 10px;
```

{% hint style="info" %}
`grid-column-gap` 在 CSS3 中，已更名為 `column-gap`。
{% endhint %}



### row-gap 設定各列間距

```css
row-gap: 20px;
```

{% hint style="info" %}
`grid-row-gap` 在 CSS3 中，已更名為 `row-gap`。
{% endhint %}



### gap 簡寫形式

```css
gap: 20px 50px; /* 第一個指的是 row-gap；第二個指的是 column-gap */
```

{% hint style="info" %}
`grid-gap` 在 CSS3 中，已更名為 `gap`。
{% endhint %}



例：

{% embed url="https://codepen.io/carlos411/pen/eYgzWbE" %}



## Container 相關屬性 - 4



### justify-items 沿著 Row Axis 排列

設定 Items 沿著 `Row(Inline) Axis` 來排列。

可設定的屬性值有：

* **`stretch`**：預設，**寬度**填滿整個 Cell。
* **`start`**：設定 Item 在自己 Cell 的左邊。
* **`end`**：設定 Item 在自己 Cell 的右邊。
* **`center`**：設定 Item 在自己 Cell 的中間。

例：

{% embed url="https://codepen.io/carlos411/pen/RwKRgEa" %}



{% hint style="info" %}
`justify-self` 是在 Grid Items 上設定，只作用於 Item 自己。
{% endhint %}



### align-items 沿著 Column Axis 排列

設定 Items 沿著 `Column(Block) Axis` 來排列。

可設定的屬性值有：

* **`stretch`**：預設，**高度**填滿整個 Cell。
* **`start`**：設定 Item 在自己 Cell 的上方。
* **`end`**：設定 Item 在自己 Cell 的下方。
* **`center`**：設定 Item 在自己 Cell 的中間。

例：

{% embed url="https://codepen.io/carlos411/pen/ExNqymR" %}



{% hint style="info" %}
`align-self` 是在 Grid Items 上設定，只作用於 Item 自己。
{% endhint %}



### place-items 簡寫形式

是 `justify-items` 和 `align-items` 的簡寫形式，格式如下：

```css
place-items: <align-items> <justify-items>;
```



{% hint style="info" %}
`place-self` 是在 Grid Items 上設定，只作用於 Item 自己。
{% endhint %}



## Container 相關屬性 - 5



### justify-content 沿著 Row Axis 排列

全部的 Items，一起沿著水平方向 `Row(Inline) Axis` 的排列，可以設定的屬性值有 7 個，如下：

* **`stretch`**：預設值。
* **`start`**：置左。&#x20;
* **`end`**：置右。&#x20;
* **`center`**：置中。
* **`space-around`**：Grid Items 之間的距離會是最左邊、最右邊的兩倍大。
* **`space-between`**：Grid Items 最左邊會靠左、最右邊會靠右，其餘距離均分。
* **`space-evenly`**：Grid Items 之間的距離及最左邊、最右邊，距離都是相同的。

例：

{% embed url="https://codepen.io/carlos411/pen/yLavPNz" %}



### align-content 沿著 Column Axis 排列

全部的 Items，一起沿著垂直方向 `Column(Block) Axis` 的排列，可以設定的屬性值有 7 個(與 `justify-content` 屬性相同)，如下：

* **`stretch`**：預設值。
* **`start`**：置頂。
* **`end`**：置底。&#x20;
* **`center`**：置中。
* **`space-around`**：Grid Items 之間的距離會是最上方、最下方的兩倍大。
* **`space-between`**：Grid Items 最上方會置頂、最下方會置底，其餘距離均分。
* **`space-evenly`**：Grid Items 之間的距離及最上方、最下方，距離都是相同的。

例：

{% embed url="https://codepen.io/carlos411/pen/yLavPOP" %}





### place-content 簡寫形式

是 `justify-content` 和 `align-content` 的簡寫形式，格式如下：

```css
place-content: <align-content> <justify-content>;
```

