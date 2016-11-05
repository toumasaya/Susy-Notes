# Gutter Position

`$susy` map 的 `gutter-position` 是指定你的 gutter 在 columns 輸出的位置，同時也指定 gutter 是以 margin 或 padding 的屬性輸出。

```scss
// scss
$susy: (
  gutter-position: after (before | after | split | inside | inside-static )
);
```

先做個摘要，詳細內容請看後面筆記：

## after

* gutter：在 element 的後面
* gutter output：margin
* span mixin output：`width` `margin-right` `float: left`
* keyword：`last`，移除該列最後一個 element 的 gutter

## before

* gutter：在 element 的前面
* gutter output：margin
* span mixin output：`width` `margin-left` `float: left`
* keyword：`first`，移除該列第一個 element 的 gutter

## split

* gutter：1/2 gutter，分別在 element 的前後兩端
* gutter output：margin
* span mixin output：`width` `margin-left` `margin-right` `float: left`
* keyword：parent element 要加上 `nest`
* 不需要移除任何 gutter

## inside

* gutter：1/2 gutter，分別在 element 的前後兩端
* gutter output：padding
* span mixin output：`width` `padding-left` `padding-right` `float: left`
* keyword：parent element 要加上 `nest`
* 不需要移除任何 gutter

## inside-static

* gutter：1/2 gutter，分別在 element 的前後兩端，gutter 為固定單位，非 %
* gutter output：padding
* span mixin output：`width` `padding-left` `padding-right` `float: left`
* keyword：parent element 要加上 `nest`
* 不需要移除任何 gutter
* 必須要設定 `column-width` 的寬度

