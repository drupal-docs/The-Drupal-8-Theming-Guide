## Seven

*Seven* 在 Drupal 7 中诞生，用做缺省的管理主题，他的设计目的是增强 Drupal 7 的用户体验。Seven 在 Drupal 8 中仍然是缺省的管理主题。使用 [Seven 样式指南](https://groups.drupal.org/node/283223)来进一步改善体验和外观。Seven 主题当前由 [Lewis Nyman](https://www.drupal.org/u/lewisnyman) 管理。

~~~yaml
base theme: classy
~~~

> 有些用户可能会奇怪，为什么这个主题不改名叫 `eight`（[D8 中重新命名](https://www.drupal.org/node/1297428)）？
> 回答是 **不**

![Seven screenshot](../img/seven.png)

### 采访 Lewis Nyman

#### Seven 主题的管理者的工作内容是什么？

有[完善的文档](https://www.drupal.org/contribute/core-maintainers#component)来说明核心组件管理者的工作内容。我的首要职责是概览 [Seven Queue](https://www.drupal.org/project/issues/drupal?component=Seven+theme) 中的所有 Issue，很少有人会做这个事情，但是只有这样，在有人报告 BUG 的时候或者发起讨论的时候，才能判断这些 Issue 是否已经存在。

我还要负责确认 Issue 已经被正确的组织，并且被有序的处理。另外，我丰富的经验确保我有能力评审 Seven 所有的补丁，检查他们的质量，确保他们的一致性。

#### Drupal 8 中的 Seven 主题有什么新特性？

Seven 的设计追随了 Drupal 8 的脚步。[Ry5n](https://www.drupal.org/u/ry5n) 、[Yoroy](https://www.drupal.org/u/yoroy) 和 [Bojhan](https://www.drupal.org/u/bojhan) 编制了一份样式指南，增强了这一主题的外观表现，同时也为很多核心模块的用户体验的提升提供了良好的基础。

有些例子还会持续使用不同的按钮类型、下拉按钮、新的内容编辑布局，以及行内的 Form 错误提示。

#### Seven 主题以后会变成怎样？对未来的 Drupal 8.1 或者 Drupal 9 已经有计划了么？

Seven 正在缓慢的向组件化设计靠拢。根据样式指南和我们的 [CSS 新标准](https://www.drupal.org/coding-standards/css)，Seven 中的很多 CSS 正在使用更加抽象、可复用的 CSS 组件。我想，Seven 会在 8.x 的组件基础上发展，以适应核心和第三方不断增长的需求。

在 Drupal 9 中，正在讨论的 [组件化设计](https://events.drupal.org/losangeles2015/sessions/drupal-9-components-library-next-theme-system)不仅仅涵盖了 CSS，而是整个 Drupal 主题系统。

如果 Drupal 9 的计划能够实现，Seven 会是这个系统的第一个测试用例。

现在的 CSS 如此强大，我们还讨论了关于向 Seven 主题增加更多的视觉效果的问题。有人开玩笑说为界面增加音效，天知道这是不是玩笑。


#### 我们刚在讨论的内容中有一部分是关于 Drupal 的样式指南，这方面的进展如何呢？

我们遇到了一些跟 [原有 Photoshop 样式指南](https://groups.drupal.org/node/283223) 有关的维护问题，要在设计实现过程中跟进是个比较痛苦的事情。

我们现在已经有了一个计划，[使用 KSS 来实现 Seven 的 CSS 组件](https://www.drupal.org/node/2404111)，这样我们可以为核心代码生成和 [api.drupal.org](https://api.drupal.org) 以及 [Drupal 核心 Javascript 文档](https://www.drupal.org/node/2182153)类似格式的样式指南。因为 KSS 的语法和现有 Drupal 的注释标准颇有不同，造成了一些障碍。在 Drupal 8 发布 RC 版本之后，HTML 和 CSS 代码会被冻结，在这之前还有很多事情要做，所以这部分内容只能推迟完成。

#### 有些人觉得这名字很古怪。你觉得呢？如果让你来命名，你会起个什么名字？

近年来，我想我已经不太在意这个名字了。我认为名字的意义是我们赋予的。大家都知道，Seven 是随 Drupal 发行的管理主题。改了名可能会更加麻烦。

如果我们现在创建了这个主题，并给他起个名字，我可能会像 Bartik 一样，用名人来命名。也许是忍者神龟中的一个。

#### 为 Drupal 创建管理主题的最大挑战是什么？

现在最大的问题是，大量的模块都需要不同的用户界面。有的模块会为了自己的需要来调整现有界面，有些甚至会从头做起。一个管理主题想要无损的支持所有的需求是个难题。

我的梦想是，在模块中完全没有管理界面的 CSS。切近一些的目标是尽量减少这种 CSS。我希望持续发展 Seven 主题，使之成为一个真正有用的界面框架，持续的影响模块开发者，利用已有的组件来编写一致的用户体验。

***

**延伸阅读**

* [官方网站的 Seven 文档](https://www.drupal.org/documentation/themes/seven)
* [Lewis Nyman](http://lewisnyman.co.uk/)
