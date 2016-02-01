## stable

缺省的基主题。

*Stable* was introduced in Drupal 8 as a backwards compatibility layer for Drupal 8's core markup, CSS and JS. When no `base theme` is provided by a theme, stable will automatically be used.

*Stable* 在 Drupal 8 中是用来作为核心标记、CSS 以及 JS 的向下兼容层而存在的。当主题没有指定基主题时，就会自动使用 Stable 主题。

> Drupal 8 核心通过这一主题提供了一个最小化的标记集。对前端开发者来说，可以在这个基础上加入更加丰富的内容，而无需去移除 Drupal 8 自带的缺省类。对 Bootstrap 或者 Foundation 这样的前端框架尤其有益。

把基主题设为 `false`，就能够禁用这种向后的兼容

~~~yaml
base theme: false
~~~

***

* 官方的变更记录：[缺省加入 Stable 基主题，保证向后兼容性](https://www.drupal.org/node/2580687)
