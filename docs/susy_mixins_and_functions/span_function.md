# Span Function

span function 和 span mixin 很像，不過 span function 輸出的 CSS 只有 `width` 屬性：

```sass
// This has a width of 3 columns out of 9 columns
.some-selector
  width: span(3 of 9)
```

span function 讓你不必再去記一堆前面設定的 margin 或 padding mixins 的寬度：

```sass
// This has a padding of 1 column out of 9 columns
.some-selector
  padding-left: span(1 of 9)
```
