# Using Context in Nested Layouts

巢狀 layout 其實很常見，例如以下：

```html
<div class="wrap">
  <div class="content">
    <!-- nested item -->
    <div class="inner-content">Nested Item</div>
  </div>
  <div class="sidebar"></div>
</div>
```

如果 `.inner-content` 要在 `.content` 底下佔取欄位，就表示你要處理 Susy 巢狀 layout 了。

如果說想把上述 HTML 處理成以下的樣子：

![](https://i.imgur.com/57m0H99.png)

`.wrap` 佔 12 columns，`.content` 佔 8 columns，`.inner-content` 佔 4 columns。

前面提過 context 就是看 parent element 所佔的 columns，所以語法可以這樣寫：

```sass
// .content takes up 8 columns. It's parent, .wrap, takes up 12 columns
.content
  @include span(8 of 12)

// .inner-content takes up 4 columns. It's parent, .content
.inner-content
  @include span(4 of 8)
```

簡單來說，知道 context 的意義，你就只要計算需要多少 columns 而已。

不過在大多數時候，context 的語意不會像上面的例子這麼明顯可見。因為一但你建構一個很大的專案時，~~懶人~~通常不會想一直重複寫出 context，會想要保持 Sass 語法的 DRY（Don't Repeat Yourself）。

下面會講到真實情況下，context 都是怎麼呈現。
