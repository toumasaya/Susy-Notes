# Context

請看以下的 `span` mixin：

```sass
// sass
.content
  @include span(8 of 12)
```

前面提過 `of` 關鍵字後面接的是 `$context` 參數，在上面的例子中，context 是 12。

如果實際來看的話：

![](https://i.imgur.com/ONXb2fC.png)

簡單來說，context 就是 parent element 的欄位（columns）數目。
