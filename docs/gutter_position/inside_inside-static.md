# inside/inside-static

`inside` 和 `inside-static` 跟 `split` 有點像，它們的 gutter 也是被拆成兩半放置在元素的前後，只是輸出的是 `padding`。同樣也不需要移除任何 gutter。

![](https://i.imgur.com/4PIsx1s.png)

如果你沒有為 parent container 設定 `nest`，children 一樣會像脫韁野馬一樣無法對齊 grid。

脫韁野馬：

![](https://i.imgur.com/XtA4i7X.png)

浪子回頭：

![](https://i.imgur.com/s4JJ5XJ.png)

當然輸出的 CSS 也跟 `split` 一樣，`.content` 會把 gutter（padding） 拿掉、合併到 `width` 裡面，但由於 `inside` 是 `padding` 模式，所以拿掉 `padding` 感覺不到 `.content` 擴展。

`inside-static` 顧名思義，就是「固定（單位）的 inside」，功能其實跟 `inside` 大同小異，不一樣的就是它的 gutter 會輸出固定單位（px, em）而不是輸出百分比（%）。

使用上簡單來說就是，設定 `inside-static` 之後，你還要再去 `$susy` map 的 `column-width` 指定寬度（px, em）。

要注意的是，此時你的 `container` 就保持 `auto`，因為當你設定了 `column-width`，Susy 就會自動幫你計算出 `container` 的寬度了。
