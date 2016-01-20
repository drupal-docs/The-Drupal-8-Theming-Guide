## Twig 调试

A new feature in Drupal core is the **Twig debug** tool. It allows developers to trace from which template files certain markup comes. To enable Twig Debugging, set the `debug` parameter in the `twig.config ` to `true`.

Drupal 核心的一个新特性就是 **Twig 调试工具**。这一工具让开发者可以通过跟踪，来得知某些标记来自于哪一个模板文件。要启用 Twig 调试，可以在 `twig.config` 文件中把 `debug` 参数设置为 `true`

![](../img/twig-debug-services.png)

**sites/default/services.yml**:

~~~yaml
parameters:
  twig.config:
    debug: true # originally false
~~~

当打开 Web 控制台时，会看到加入了 HTML 注释：

~~~html
<!-- FILE NAME SUGGESTIONS:
   * html--front.html.twig
   * html--.html.twig
   x html.html.twig
-->
<!-- BEGIN OUTPUT from 'core/modules/system/templates/html.html.twig' -->
~~~

![](../img/twig-debug-example.png)

> **Drupal 7** 中也有类似功能。可以通过在 `settings.php` 设置  `$conf['theme_debug'] = TRUE;` 来激活此功能。

### 模板建议

The files with **(\*)** are theme hook suggestions, and can be used to override the template file in more specific and less generic use cases. The file marked with **(x)** is template file that is currently being used to print the markup. The comments end with the file that is currently being using to print the markup.

带有**（\*）**的文件是主题建议，在特定条件下可以用来覆盖模板文件。 带有**（x）**的文件是当前正在使用并输出被跟踪标记的模板。注释中最后一个文件是用于指出最后输出的模板。

    <!-- FILE NAME SUGGESTIONS:
       * html--front.html.twig
       * html--.html.twig
       x html.html.twig
    -->
    <!-- BEGIN OUTPUT from 'core/modules/system/templates/html.html.twig' -->

### 调试变量


要输出（模板文件中）所有的可用变量，可以使用 `dump()` 函数。要获取一个特定变量的内容，只要把变量传递给这个函数即可。

> **注**：当使用 `dump()` 的时候，可能会遭遇白屏。这个命令会递归遍历和输出所有变量，造成大量内存消耗。

~~~twig
# 只输出可用键
{{ dump(\_context|keys) }}
~~~

输出**全部**可用变量

~~~twig
{{ dump() }}
~~~

> **注**：同下面的 `dump(_context)` 等效。

输出 `$foo` 变量：

~~~twig
{{ dump(foo) }}
~~~

输出 `$foo` 和 `$bar` 变量：

~~~twig
{{ dump(foo, bar) }}
~~~

在所有的 Twig 模板中都有两个**全局变量**：

* `_context`, which contains all variables that are passed to the template file. When using `dump()` without passing in a variable, the `_context` will be printed.

* `_context`，包含了传递给这一模板文件的所有变量。当不带有参数使用 `dump()` 的时候，就会输出 `_context`。

* `_charset` 代表当前的字符集。

### Devel 和 Kint

`dump()` 在调试单个变量的时候很好用，但是在输出所有变量的时候就比较辛苦了。这就是使用 [**Devel** module](https://www.drupal.org/project/devel) 的时机了。这个**第三方**模块包含很多的子模块，其中一个就是 **Kint**，它提供了一个友好的界面来展现调试数据。

~~~bash
# 下载 Devel 模块
drush dl devel
# 启用 Devel 以及 Kint 模块
drush en devel kint
~~~

激活之后，可以使用 `kint()` 来替换所有的 `dump()` ，以获得更好的调试体验。

---

**延伸阅读**

* [在 Twig 模板 中加入 Kint 支持](https://www.drupal.org/node/2218949)
* [在 Twig 模板中发现和查看变量](https://www.drupal.org/node/1906780)
* [调试编译后的 Twig 模板](https://drupal.org/node/1903374)
