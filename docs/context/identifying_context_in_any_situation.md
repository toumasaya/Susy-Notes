# Identifying Context In Any Situation

前面提過，如果你想要找出 context，就去看 `span()` mixin（或是其他 Susy mixin），然後去看接在 `of` 後面的參數：

```sass
// sass
.content
  @include span(8 of 12)
```

上面的例子中，context 是 12。

但多數你可能會看到 context 被選擇性忽略的情況，也就是 `span()` mixin 只有寫出 `$span` 的值、或只有 `last` 之類的關鍵字：

```sass
// sass
.content
  @include span(8)

.sidebar
  @include span(4 last)
```

在這種情況下 Susy 它會往上層去找需要的 context。

第一個 Susy 會先去找 `span()` mixin 是否有被 `nested()` 或是 `with-layout()` mixin 包覆起來，例如：

```sass
// sass
@include nested(8)
  .inner-content
    @include span(4)
```

上述的寫法其實就等於：

```sass
// sass
.inner-content
  @include span(4 of 8)
```

`nested()` mixin 可以讓你方便的切換 context。

如果你想讓某個區塊套用其他的 layout，就可以使用 `with-layout()`：

```sass
// scss
$new-susy-map: (
  columns: 16,
  gutters: 1/22,
  gutter-position: split,
);

@include with-layout($new-susy-map) {
  // altered grids within here
}
```

如果 Susy 找不到 `nested()` 或是 `with-layout()` mixin，Susy 就會去 `$susy` map 裡面取用 context：

```sass
// scss
$susy: (
  columns: 12,
);

.inner-content {
  @include span(4);
}
```

上面的語法等於：

```sass
// scss
.inner-content {
  @include span(4 of 12);
}
```

喔喔！根據前面的例子，你可以發現這是錯誤的呈現，因為 `.inner-content` 應該要`span(4 of 8)` 才對。

所以一但了解 context 背後的原理，你就知道要怎麼運用以及除錯了。
