每個 Susy 專案一開始都需要設定 `$susy` map：

```scss
// scss
// 因為 sass 的語法限制，map 設定變成只能寫成一行
// 所以個人習慣寫到有關 map 的設定時，使用 scss 寫法比較省事，也容易閱讀
$susy: (
  key: value,
  key: value2
);
```

Susy 預設的 map：

```scss
$susy: (
  flow: ltr,
  math: fluid,
  output: float,
  gutter-position: after,
  container: auto,
  container-position: center,
  columns: 4,
  gutters: .25,
  column-width: false,
  global-box-sizing: content-box,
  last-flow: to,
  debug: (
    image: hide,
    color: rgba(#66f, .25),
    output: background,
    toggle: top right,
  ),
  use-custom: (
    background-image: true,
    background-options: false,
    box-sizing: true,
    clearfix: false,
    rem: true,
  )
);
```

其中要注意的是 Susy 預設採用的 box model 為 `content-box`，但建議還是使用 `border-box` 比較省事。如果設定成 `border-box`，別忘了記得要再 import `border-box-sizing` 告訴瀏覽器 box model 的類型。
另外可以開啟 `debug` 模式，讓你在開發階段可以針對 grid 除錯：

```scss
// scss
$susy: (
  global-box-sizing: border-box,
  debug: (image: show)
);

@import border-box-sizing;
```
