# after

Susy 預設的 `gutter-position` 是 `after`。

`after` 會在每個 column 後面加上 gutter，所以你必須在那一列的最後一個 column 移除 gutter。

`after` 輸出的 gutter 會是 `margin` 屬性。

![](https://i.imgur.com/gYwLPep.png)

當你使用 `after` ，`span` mixin 會輸出三個 CSS 屬性：`width`、`margin-right`、`float: left`。

```sass
// sass
.test
  @include span(3 of 4)
  
// output
.test {
  width: 73.68421%;
  float: left;
  margin-right: 5.26316%;
}
```

可以使用 `last` 關鍵字移除最後一個元素的 gutter，這樣最後一個元素的 `margin-right` 就會是 `0`，同時最後一個元素會被設成 `float: right`：

```sass
// sass
.last
  @include span(1 of 4 last)

// output
.last {
  width: 21.05263%;
  float: right;
  margin-right: 0;
}
```
