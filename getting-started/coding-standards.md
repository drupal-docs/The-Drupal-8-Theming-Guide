## 编码规范

下面是 **CSS**、**javascript** 以及新加入的 **Twig** 模板引擎的编码规范

- [CSS 编码规范](https://www.drupal.org/node/1886770).
- [Javascript 编码规范](https://www.drupal.org/node/172169).
- [Twig 编码规范](https://www.drupal.org/node/1823416).

## CSS

CSS 编码规范来源于 **SMACSS** 以及 **BEM** 这两种知名的方法论。

### SMACSS

SMACSS（读作 "smacks"）标准是**可扩展的、模块化的 CSS 架构**。Drupal 8 使用 **SMACSS** 对 CSS 进行概念上的组织。

#### Base

> **Base** 通常包含 [css reset](http://cssreset.com/scripts/eric-meyer-reset-css/) 或者 [normalize](http://cssreset.com/scripts/normalize-css/)，以及 HTML 元素样式。Drupal 8 在 *system* 模块中包含了 **normalize.css**。

#### 布局（Layout）

> **Layout** 规则定义了通用模块在各个页面上的典型呈现方式。**Grid 系统**中的 CSS 也在这一类别中。

在 Drupal 核心主题中，所有的布局样式类（全局页面布局）都以 `.layout-` 为类名的前缀。举例如下：

~~~css
    .layout-content
    .layout-container
    .layout-sidebar-left
    .layout-sidebar-right
~~~

**注**：这些 `.layout-` 类绝不应该包含 colors、borders 等内容，而只推荐包括 width、loats、margins 以及 paddings 这类内容，仅满足全局的页面 Grid 布局需求即可。

#### 组件（Components）

**SMACSS** 官方称之为 **module**，然而 *modules* 在 Drupal 中使用已久，所以为防止冲突，这里将其重命名为 **组件（Components）**。

> **组件** 是独立的可复用的 UI 元素。组件规则应该有弹性、可复用。例如对话框、轮播、微件等。

#### 状态（State）

> **状态**以参数化的形式覆盖所有其他的样式。一般用来描述某种动作或者触发器。最好的例子是 `is-active` 状态，用来标识是否激活。这些类一般用 `is-` 作为前缀。

在 Drupal 核心中，状态通常和组件一起定义。

#### 主题（Theme）

为了防止和 Drupal 的 **Themes（主题）**相混淆，也会使用 **skin（皮肤）**的叫法。

> **主题** 定义了颜色和图像，为前面的任何元素提供视觉支持

例如下面的代码：

~~~css
    // component.css

    .component {
        border: 1px solid;
    }

    // theme.css

    .component {
        border-color: blue;
    }
~~~


在 [SMACSS](https://smacss.com/) 可以进一步了解相关知识。

![MortenDK approved](../img/mortendk.jpg)

#### Seven 主题 中的 SMACCS

主题 “Seven” 用了这些分类来拆分 CSS 规则。Seven 主题包含了一个叫 `css` 的目录，在这个目录中有四个子目录：

- `core/themes/seven/css/base`
- `core/themes/seven/css/components`
- `core/themes/seven/css/layout`
- `core/themes/seven/css/theme`

### BEM

BEM (Block Element Modifier 块元素修饰符) 是一种命名原则。基于 **BEM 方法论** 的 Drupal 8 CSS 类命名更加清晰易读。

例如：

~~~css
.block__element--modifier
~~~

- **Block（块）** 是一个独立实体，表现了页面中的一个片段的界面。
- **Element（元素）** 是 Block 的一部分，表达 Block 的功能和语义。其有效性仅限于所属 Block 的范围。Block 不一定包含 Element。
- **Modifier（修饰符）** 是 Block 或 Elements 的标志（属性），他对属性以及状态进行了定义。他可以是布尔值（例如：visible: true 或者 false），也可以是键值对（size: large, medium, small）- 有点像 HTML 的属性，不过不完全相同。如果一个项目有多个属性，可以包含多个修饰符。

**来源**： [Smashing Magazine](http://www.smashingmagazine.com/2014/07/17/bem-methodology-for-small-projects/)

`buttons.theme.css (Seven)`:

- `.button {}`,  **块**。
- `.button--primary {}`, **修饰符**。

`node.css (Seven)`:

- `.node__submitted {}`,  **元素**。

***

**延伸阅读**

* [SMACSS 主页](https://smacss.com)
* [Split Seven's style.css into SMACSS categories（把 Seven 的 style.css 拆分为 SMACSS 分类）](https://www.drupal.org/node/2321505), **Seven** 主题按照新的编码规范重构的过程。
* [Organize Your Styles - An Introduction to SMACSS（组织你的样式 -- SMACSS 简介）](https://www.acquia.com/blog/organize-your-styles-introduction-smacss), Acquia 的博客。
* [BEM and SMACSS: Advice From Developers Who’ve Been There（BEM 和 SMACSS：先行者的忠告）](http://www.sitepoint.com/bem-smacss-advice-from-developers/), New Relic 的博客。
* [BEM methodology for small projects（面向小项目的 BEM 方法）](http://www.smashingmagazine.com/2014/07/17/bem-methodology-for-small-projects/)
