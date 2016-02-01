# Drupal core themes

Drupal 8 的四个**核心**主题位于 `core/themes` 文件夹内。这些主题是 Drupal 8 移动提案的一部分，因此他们都是响应式的。所有的核心主题（不是基主题）都能充当管理主题进行使用。因为 Drupal 8 是多语言的，所以核心主题也都支持双向文字。

> **注：** Stark 主题中有一个用于响应式布局的样式表。后来这些样式被清除掉了。 **在 Stark 一节中可以了解这部分内容**

- **bartik**: *移动优先的响应式主题，有弹性，可定制颜色，带有很多的区块。*
- **seven**: *Drupal 8 的缺省管理主题，具有干净的线条，简单的块，使用 sans-serif 字库，便于管理工作的进行。*
- **stark**: *一个几乎没有样式的主题，用来演示 Drupal 缺省的 HTML 和 CSS*

上述三个 Drupal 7 主题你可能还是有印象的，不过还有另外两个

- **classy**: [[meta] Results of Drupalcon Austin's Consensus Banana](https://www.drupal.org/node/2289511): 在 2014 年的奥斯汀 DrupalCon 中，认为需要在核心中加入新的主题。Classy 是 Seven 以及 Bartik 的基主题。
- **stable**: Stable 主题作为 Drupal 8 核心标记、CSS 以及 JS 的向后兼容的布局而存在。如果一个主题的 `.info.yml` 文件中没有注明基主题，则会使用该主题作为基主题。
----

下面是一个概括，说明 Drupal 8 主题之间的关系。

![An overview of the core themes](../img/theme-overview.png)
