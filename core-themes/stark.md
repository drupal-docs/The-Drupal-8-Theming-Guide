## Stark

**Stark** 这一核心主题演示了 Drupal 的缺省标记。他不包含任何的模板或 CSS 文件。也就是说他使用的是 Drupal （核心）模块的模板和 CSS 文件。

> 为了避免混淆 Drupal 和 第三方模块加入到页面里的 CSS，Stark 主题除了 “页头、侧栏、内容以及页脚” 布局之外，没有加入其他样式。这是受 Drupal 8 移动提案的影响，[Start 在 Drupal 8 中使用了响应式布局](https://www.drupal.org/node/1322794)，这一响应式布局的 CSS 规则可以在 `css/layout.css` 中找到。

> 在 Drupal 7 中，Stark 包含了布局和页面区块所使用的 CSS。起初 Stark 布局也是响应式的，但是后来 CSS 被移除了（[从 Stark 中删除所有视觉(元素)](https://www.drupal.org/node/2349711)）。因此，Stark 现在只输出 HTML 以及模块中的 CSS 了。


**Stark** 对 **开发人员** 来说很有用，用来判断模块相关的 CSS 和 JavaScript 是否影响到了复杂的主题。对于 **设计人员** 来说，他可以在学习 Drupal 标记的时候避免额外的干扰。

> 总而言之，Stark 输出的是 Drupal 最基础的 CSS 和 HTML。

![Stark screenshot](../img/stark.png)

***

**延伸阅读**
