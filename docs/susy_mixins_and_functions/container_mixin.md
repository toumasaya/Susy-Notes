# Container Mixin

## 何謂 container？

Grid 都需要一個 grid container，想像一下你有個抽屜，抽屜裡裝著許多不同大小的收納盒，container 就是抽屜。

container 的 CSS `class` 可以任意取名，常見的就是 `.wrap` 或是 `.container`。

## 定義 container

```sass
// The Container Mixin
@include container( [<length>] )

// Note: Optional arguments are enclosed in []
```

`<length>` 參數為選擇性，可以設定 container 的 max width。如果沒有設定，Susy 會使用預設的 `max-width: 100%`。

## `container()` 輸出的 CSS

container 的作用就是把你的內容置中，為了置中，會需要三個 CSS 屬性：`width`、`margin-left`、`margin-right`，如果需要 responsive，`width` 就要改成 `max-width`。

所以以前要寫置中、responsive 會這樣寫：

```sass
// sass
.wrap
  max-width: 960px
  margin-left: auto
  margin-right: auto
```

使用 Susy 的 `.container()` mixin 就會幫你產生上述需要的 CSS 屬性：

```sass
// sass
.wrap
  @include container()
  
// output
.wrap {
max-width: 100%;
margin-left: auto;
margin-right: auto;
/* Other properties... */
}
```

## 自定義 container 寬度

前面提過 Susy 預設的 container 寬度是 100%（auto），如果你想要設定 container 的最大寬度，例如 1140px，可以設定 Susy map 的 key `container`：

```sass
// scss
$susy: (
  columns: 4,
  container: 1140px,
  global-box-sizing: border-box,
  debug: (image: show)
);

// output
.wrap {
  max-width: 1140px;
  margin-left: auto;
  margin-right: auto;
  /* Other properties... */
}
```

或是直接寫在 mixin 裡覆蓋 map 的設定：

```sass
@include container(1140px)
```

## `container()` 還會產生什麼？

`.container()` mixin 除了幫你把 container 置中，它還幫你產生兩組有用的屬性。

第一組是會幫你在 container 加上 `clearfix`：

```css
/* Css */
.wrap:after {
  content: " ";
  display: block;
  clear: both;
}
```

`clearfix` 確保 container 不會因為裡面的子元素含有 `float` 屬性而造成 collapse。這很重要，因為畢竟 Susy 就是使用 `float` 建構 grid system。

第二組就是 grid background 的 CSS：

```css
/* Css */
.wrap {
  background-image: linear-gradient(to right, rgba(102, 102
  background-size: 26.31579%;
  background-origin: content-box;
  background-clip: content-box;
  background-position: left top;
}
```

不過你要開啟 `debug: (image: show)` 才會出現這些屬性。
