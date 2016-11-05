# before

`before` 會在每個 column 前面加上 gutter，所以你必須移除那一列的第一個 column 的 gutter。

`before` 輸出的 gutter 會是 `margin` 屬性。

![](https://i.imgur.com/zbvDUIF.png)

當你使用 `before` ，`span` mixin 會輸出三個 CSS 屬性：`width`、`margin-left`、`float: left`。

```sass
// sass
.test
  @include span(3 of 4)
  
// output
.test {
  width: 73.68421%;
  float: left;
  margin-left: 5.26316%;
}
```

可以使用 `first` 關鍵字移除第一個元素的 gutter，這樣第一個元素的 `margin-left` 就會是 `0`：

```sass
// sass
.first
  @include span(1 of 4 first)

// output
.first {
  width: 21.05263%;
  float: left;
  margin-left: 0;
}
```
