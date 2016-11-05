# Susy Notes

這個系列筆記是看了來自於 [Zell blog](https://zellwk.com/blog/) 的 [Susy 系列文章](https://zellwk.com/tags/susy/)，經過理解再自己做成筆記。

另外 Zell 有提供免費的電子書 [Learning Susy](http://learnsusy.zellwk.com/)，對於想要了解 Susy 基本知識我覺得還蠻簡單易懂的。

## 事前準備

環境安裝基本上就是要有 Ruby、Sass、Susy。
要用 Sass 或 Scss 寫 Susy 端看個人習慣，只是在設定 Susy map 時，礙於 Sass 寫法的限制，我會比較習慣用 Scss 寫 map 設定。

最重要的當然是要 import Susy：

```scss
// sass
@import susy
```
## 目錄

* [Susy Map](docs/susy_map/susy_map.md)
   * [Using the Susy Map](docs/susy_map/using_the_susy_map.md)
* [Susy mixins and functions](docs/susy_mixins_and_functions/susy_mixins_and_functions.md)
   * [Container Mixin](docs/susy_mixins_and_functions/container_mixin.md)
   * [Span Mixin](docs/susy_mixins_and_functions/span_mixin.md)
   * [Span Function](docs/susy_mixins_and_functions/span_function.md)
   * [Gutter Function](docs/susy_mixins_and_functions/gutter_function.md)
* [Gutter Position](docs/gutter_position/gutter_position.md)
   * [after](docs/gutter_position/after.md)
   * [before](docs/gutter_position/before.md)
   * [split](docs/gutter_position/split.md)
   * [inside/inside-static](docs/gutter_position/inside_inside-static.md)
* [Context](docs/context/context.md)
   * [Using Context in Nested Layouts](docs/context/using_context_in_nested_layouts.md)
   * [Identifying Context In Any Situation](docs/context/identifying_context_in_any_situation.md)

## 筆記參考來源

強烈建議先跟著教學 [A Complete Tutorial to Susy 2](https://zellwk.com/blog/susy2-tutorial) 實際做一遍。

* [A Complete Tutorial to Susy 2](https://zellwk.com/blog/susy2-tutorial)
* [A Complete Tutorial to Susy 2 (Part 2)](https://zellwk.com/blog/susy2-tutorial-2)
* [Understanding Gutter Positions in Susy](https://zellwk.com/tags/susy/page-2/)
* [Fix 90% of Your Problems With Susy by Getting This One Concept Right](https://zellwk.com/blog/context-with-susy)
