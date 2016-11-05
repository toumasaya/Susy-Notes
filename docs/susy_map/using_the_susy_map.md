# Using the Susy Map

設定好 Susy map 之後，你就可以使用 Susy 相關的 mixins 或 functions（關於這兩者，之後會提到）。

例如先新增一個 `div.wrap` 的元素，然後在 Sass 中把它設定為 `container`：

```html
<!--html-->
<div class="wrap"></div>
```
```sass
// sass
.wrap
  @include container() // 如果沒有參數，() 可以省略
  height: 100vh // 這是強制讓 .wrap 的高度撐高到 100%，因為預設中 .wrap 是不會有高度的，除非你自行設定
```

然後你的畫面就會長這樣：

![](https://i.imgur.com/IGnXeIK.png)

開啟 `debug` 之後，畫面就會出現有顏色的 grid background，當然顏色樣式也可以自訂。
