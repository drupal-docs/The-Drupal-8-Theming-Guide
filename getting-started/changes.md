## Drupal 核心

`/core` 是 Drupal 的核心所在。Drupal 根目录中的 `/modules` 以及 `/themes` 用于包含自开发和第三方模块。核心主题包含在 `/core/themes` 目录中。

## HTML5

Drupal 8 的标记使用 [HTML 5](http://buytaert.net/html5-in-drupal-8) 实现。在核心中使用了 `header`、`nav` 以及 `article` 等新标记。

**延伸阅读**：
- [The Drupal HTML5 Group](https://groups.drupal.org/html5)

## 可用性

加入了 [WAI-ARIA Roles](https://www.drupal.org/node/1179668) 角色。这是一系列的角色、状态以及事物，可用于提供丰富的语义，提高可访问性以及交互能力。WAI-ARIA 在 xhtml 1.0 中是无效的，但在 HTML5 中是有效的，能够应用在 Drupal 8 的标记之中。利用 HTML 元素的角色属性，作者可以为页面组件提供更多的目的信息。

## 响应式

Drupal 8 是一个开箱可用的移动友好、响应式设计的系统。

**延伸阅读**：
- [Drupal is now out-of-the-box responsive and mobile ready.](https://groups.drupal.org/mobile/drupal-8)

## 浏览器支持

Drupal 8 在管理界面中用 SVG 代替 PNG，用以提供分辨率无关的图标。对于 **IE 8 以及更早版本**，以及 **Android 浏览器 2.3 以及更早版本**，或类似的不支持 SVG 的浏览器，不提供相应的兼容支持。

因为不再支持这些过时的浏览器，Drupal 核心中的 CSS 得以更进一步。不再需要添加 `odd`、`even`、`first` 以及 `last` 这样的类；CSS3 伪类选择器可以完成这些任务。

**延伸阅读**：

- [Drupal 8 does not support browsers that do not support SVG（ Drupal 8 不支持不兼容 SVG 的浏览器）](https://www.drupal.org/node/2298227)
- [Most first/last/odd/even classes removed in favor of CSS3 pseudo selectors（ 按照 CSS3 的伪类选择器风格，绝大多数 first/last/odd/even 类被移除）](https://www.drupal.org/node/2178215)

***

**延伸阅读**


> 在熟悉 Durpal 7 的读者眼中会有更多不同，对主题作者来说，所有重要的变更记录都可以在[这里](https://www.drupal.org/list-changes/published/drupal?keywords_description=&to_branch=&version=&created_op=%3E%3D&created%5Bvalue%5D=&created%5Bmin%5D=&created%5Bmax%5D=&impacts%5B%5D=3)找到。