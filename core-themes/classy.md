
## Classy

~~~html
<div class="do-not-add-classes-in-drupal-core"></div>
~~~


2014 年奥斯汀 DrupalCon 上提出对新的核心基主题的需求。这一需求后来成为  **Consensus 
Banana** 的一部分。

### 共识之蕉（Consensus Banana）

> **香蕉** 从哪里来？

> 奥斯汀 DrupalCon 之前两年的一个 BadCamp 上，John Albin（[JohnAlbin](https://www.drupal.org/u/johnalbin)）在海盗节前夕手持一把塑料剑，这把剑称为共识之剑。Moten ([mortendk](https://www.drupal.org/u/mortendk)) 在会上经常手持一根香蕉指向他人提问 “所以我们就 x 问题达成共识了？”，这就是共识之蕉的由来。说的就是一个可用于指点的工具。

*Scott Reeves*

#### Meta issue

下面是一个对 [Meta issue](https://www.drupal.org/node/2289511) 的概述。

> 创建一个名为 "classy" 的核心基主题，包含目前所有核心模板的文件，。然后修改所有的核心/模块模板文件，把其中的类做最小化处理（仅包含有用部分）。然后确保 Seven 和 Bartik 能够正常工作。

#### 技术更新

技术的角度来说：移植核心类到 Classy 基主题。这一工作分成两个步骤：第一阶段，把 preprocess 函数中把类移动到核心模板文件中；第二阶段，把包含所有类的核心模板文件转到 Classy 中，这样就保证了核心模板中不再有这些内容。接下来就可以再认为所有核心模板文件都不再使用 class 了（核心中不再使用 `class="whatever"` 了）。

主题开发者不再需要一个类似 [mothership](https://www.drupal.org/project/mothership) 这样的基主题来清理多余的 div 了。调查表明，不是所有的主题开发者都需要这些一致的标记，他们不需要那么多的 `<div>`。感谢 Classy，不再需要在反抗核心上继续浪费精力了。一些主题开发者在开发自己的主题的时候，需要利用 Classy 获得有用的缺省类；而另一些开发者需要能够从头开始，不需要进行重载就获得完全的控制，拜托 Drupal 7 时代的阴影。

### Classy，新的基主题

在阿姆斯特丹 DrupalCon 上，**classy.info.yml** 由 Dries 提交到了 Drupal 8 核心中。[变更记录](https://www.drupal.org/node/2337467)

这意味着 Classy 是新的核心`基主题`，Bartik 和 Seven 都以该主题为基础派生而来。

[classy.info.yml 加入核心，并成为 Bartik 和 Seven 的基主题](https://www.drupal.org/node/2329501)

### 向后兼容性

Classy 遵从 Drupal 8 的规则，提供可靠的向后兼容性。

***

**延伸阅读**

* Modules Unraveled, episode 119: [The Classy Base Theme for Drupal 8 with Scott Reeves and David Hernandez](https://www.youtube.com/watch?v=uIutb2-Vc50).
* The official change record: [Added a new base theme to core called Classy](https://www.drupal.org/node/2337467)
