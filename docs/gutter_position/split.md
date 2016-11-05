# split

`split` 會把 gutter 拆成一半，分別置於元素的前後。

`split` 輸出的 gutter 會是 `margin` 屬性。不需要移除任何 gutter。

![](https://i.imgur.com/uKTAbuE.png)

所以可以寫成：

```sass
// sass
.content
  @include span(3 of 4)

.sidebar
  @include span(1 of 4)
```

就會長這樣：

![](https://i.imgur.com/1t31Rkk.png)

看起來一切順心，不過如果 `.content` 或 `.sidebar` 裡面有 children element 會怎樣？

首先加幾個 children 到 `.content` 底下：

```html
<!--html-->
<div class="content">
  <h1>Content</h1>
  <div class="child-one"><h2>Child One</h2></div>
  <div class="child-two"><h2>Child Two</h2></div>
</div>
```

然後讓 `.child-one` 佔 2 columns，`.child-two` 佔 1 column：

```sass
// sass
.content
  @include span(3 of 4)

.child-one
  @include span(2 of 3)

.child-two
  @include span(1 of 3)
```

結果長這樣：

![](https://i.imgur.com/RyP2hiF.png)

你可以發現 children 並沒有對齊 grid。

所以使用 `split` 時要注意 parent 和 children 的 contexts。
在這個例子中，`.content` 是 parent，`.child-one`、`.child-two` 是 children。
Susy 在處理這兩種 context 時的方式會不一樣。

來看一下輸出的 CSS：

```css
/* css output 1*/
.content {
  width: 70%;
  float: left;
  margin-left: 2.5%;
  margin-right: 2.5%;
}

.child-one {
  width: 60%;
  float: left;
  margin-left: 3.33333%;
  margin-right: 3.33333%;
}

.child-two {
  width: 26.66667%;
  float: left;
  margin-left: 3.33333%;
  margin-right: 3.33333%;
}
```

怎麼解決呢？

使用 `nest` 關鍵字告訴 Susy，`.content` 是 parent：

```sass
// sass
.content
  @include span(3 of 4 nest) // The nest key is needed

.child-one
  @include span(2 of 3)

.child-two
  @include span(1 of 3)
```

最後長這樣：

![](https://i.imgur.com/Tezmgt7.png)

children 順利對齊 grid 了。
不等等，對你沒看錯，`.content` 同時也向左右兩邊擴展半個 gutter。

可以實際看一下最終輸出的 CSS：

```css
/* css output 2 */
.content {
  width: 75%;
  float: left;
}

.child-one {
  width: 60%;
  float: left;
  margin-left: 3.33333%;
  margin-right: 3.33333%;
}

.child-two {
  width: 26.66667%;
  float: left;
  margin-left: 3.33333%;
  margin-right: 3.33333%;
}
```

比對之前的 CSS，會發現 CSS output 2 `.content` 的 gutter（margin） 寬度被拿掉，並且合併到 `width` 裡。

放在一起看：

```css
/* css output 1*/
.content {
  width: 70%;
  float: left;
  margin-left: 2.5%;  /* gutter */
  margin-right: 2.5%; /* gutter */
}

/* css output 2 */
.content {
  width: 75%;
  float: left;
  /* gutter is gone! */
}
```

所以這就是為什麼 `.content` 寬度會擴展。

總之記得如果使用 `split`，遇到 parent container，要幫它加上 `nest`。
