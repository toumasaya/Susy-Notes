# Span Mixin

## 何謂 Span？

剛剛講過 container 就像個抽屜，而 span 就是抽屜裡的收納盒。

當你使用 `span()` mixin 的時候，Susy 會輸出三種 CSS 屬性，這三種屬性會取決於你在 `span()` mixin 使用的參數以及你在 `$susy` map 裡的設定。

三種屬性：

* `width`：元素的寬度（使用 %）
* `float`：元素的浮動（left or right）
* `margin` 或是 `padding`

影響 Span 最多的是 `$susy` map 的 `gutter-position` 設定，後面會講到。

## 定義 Span

```sass
@include span( <width> [<wide / wider>] of <layout> [<last>] )
```

* `<width>` ：元素要佔用的 column number
* `[<wide / wider>]` ：選擇性參數，可以擴展 column 的寬度，擴展的基準為 1 個 gutter
* `of` ：是一個關鍵字，告訴 Susy：「嘿！接下來有個 layout 長這樣，以下是 ...」
* `<layout>` ：container 的 context（情境），context 來自於 parent container 的 column number
* `[<last>]` ：選擇性參數，告訴 Susy 這個元素是 row 中的最後一個

## 範例

```sass
// This has a width of 3 columns + 1 gutter, out of 9 columns 
// and is supposed to be the last item within the context.

.some-selector
  @include span(3 wide of 9 last)
```

上述範例講得白話一點就是：

* context：9 columns
* width：3 columns + 1 gutter
* last: the last element in the context

用英文描述比較簡單一點，所謂的 context 指的就是在當下的那個情境（在這裡的範例就是指 9 columns），之後會提到 context 的概念，如果能了解 context 會對 Susy 的運用更上手。

或是想成類似 JavaScript 的 Scope 可能比較好理解。
