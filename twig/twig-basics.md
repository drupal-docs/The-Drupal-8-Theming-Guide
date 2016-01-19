## Twig 基础

### 启用 Twig 的自动转义

> 字符串转义的意思是减少字符串中的歧义字符。

（Drupal 在）缺省情况下[启用 Twig 的自动转义](https://www.drupal.org/node/2296163)。这意味着 Twig 模板输出的字符串（ `{{  }}` 之间的内容 ）都是被转义处理过的。

### 输出一个变量

用 `{{ 变量 }}` 的方式输出模板中的一个变量，例如 ` {{ foo }}`

句点 （`.`）用于访问对象的属性：

~~~twig
{{ foo.bar }}
~~~

> （上面的语句，）Twig 会自动进行如下尝试：

~~~php
// 数组键。
$foo['bar'];
// 对象属性。
$foo->bar;
// 对象方法。
$foo->bar();
// 对象属性的 Getter。
$foo->getBar();
// 尝试 is + 方法名。
$foo->isBar();
// isset 和 get 方法
`$foo->__isset('bar');`
`$foo->__get('bar');`
~~~

*PHP*

~~~php
$awesome_array = array(
  'a_key' => 'a_value',
  'another_key' => array(
    'foo' => 'bar',
  ),
);
~~~

*Twig*

~~~twig
{{ awesome_array.a_key }} # 返回 'a_value'
{{ awesome_array.another_key.foo }} # 返回 'bar'
~~~

### Twig 过滤器（ filter ）

可以在输出变量之前用过滤器对变量进行处理，使用方式是： `{{ variable|filter }}`。

#### Twig 自有过滤器

下面是一些 Twig 引擎自带的过滤器的例子。

- `|length`，返回字典或序列类型数据的数量，或者字符串的长度。
- `|lower`，把值转换为小写。
- `|upper`，把值转换为大写。
- …

[缺省 Twig 过滤器的完整列表](http://twig.sensiolabs.org/doc/filters/index.html)。

#### Drupal 过滤器

Drupal 提供了额外的过滤器。

##### 翻译过滤器

- `t`：这个过滤器会使用 Drupal `t()` 函数处理变量，该函数会返回一个翻译结果，例如：

~~~twig
{% raw %}
<a href="{{ url('<front>') }}" title="{{ 'Home'|t }}" rel="home" class="site-logo"></a>
{% endraw %}
~~~

- `passthrough`
- `placeholder`

为了安全的对 `{% trans %}` 标记中检测到的变量进行转义，缺省情况下会使用 `@` 前缀。要传递变量（**!**）或者使用占位符（**%**），可以使用 `passthrough` 或 `placeholder` 过滤器。

- **passthrough** gets no sanitization or formatting and should only be used for text that has already been prepared for HTML display.
- **placeholder** 会转义为 HTML 并使用 [`drupal_placeholder()`](https://api.drupal.org/api/drupal/core%21includes%21bootstrap.inc/function/drupal_placeholder/8) 格式化，并显示为 `<em>emp</em>` 的形式。

- `raw` 会显示原始数据（也就是不做转义处理）。

##### 替换 Twig 的自有过滤器

- `drupal_escape` 是 Twig 的转义过滤器的替代品。参见 [`TwigExtension::escapeFilter`](https://api.drupal.org/api/drupal/core!lib!Drupal!Core!Template!TwigExtension.php/function/TwigExtension%3A%3AescapeFilter/8)

##### 实现安全的字符串连接

- `safe_join` 用于安全的连接多个字符串。参见 [`twig_drupal_join_filter`](https://api.drupal.org/api/drupal/core%21themes%21engines%21twig%21twig.engine/function/twig_drupal_join_filter/8)。

##### 数组过滤器

- `without` 创建一个可渲染数组的拷贝，并根据过滤器的参数移除指定的子元素。这样这个拷贝就可以在没有这些元素的情况下被输出；而原有的可渲染数组还可以在模板中继续被输出（带有全部子元素）。

##### CSS 和 ID 过滤器

- `clean_class` 会把字符串转换为一个有效的 HTML 类名。[使用 Html::getClass](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Component%21Utility%21Html.php/function/Html%3A%3AgetClass/8)
- `clean_id` 把字符串转换为有效的 HTML ID。[使用 Html::getId](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Component%21Utility%21Html.php/function/Html%3A%3AgetId/)

#### 翻译

Twig 的 i18n 扩展允许把模板的一部分标记为可翻译内容。我们以下面的代码为例：

~~~twig
{% trans %} Hello world {% endtrans %}
~~~

可以在可翻译字符串中间利用 `{{ variable }}` 语法嵌入变量，

~~~twig
{% trans %} Hello {{ name }} {% endtrans %}
~~~

要在可翻译块中使用过滤器对变量进行处理，可以首先把过滤器结果赋值给一个变量。

~~~twig
{% set name = name|capitalize %}

{% trans %}
  Hello {{ name }}!
{% endtrans %}
~~~

可翻译字符串可以有复数操作，只要实现一个 `{% plural ... %}` 开关就完成了：

~~~twig
{% trans %}
  Hello star.
{% plural count %}
  Hello {{ count }} stars.
{% endtrans %}
~~~


#### 注释

~~~twig
{# 用这一对标记来包含注释 #}
~~~

#### 条件判断 （此处原文为 Function，疑似错误）

`if` ：

~~~twig
{% if site_slogan %}
  <div class="site-slogan">{{ site_slogan }}</div>
{% endif %}
~~~

#### 循环

一个 `for` 循环。输出结果为 `0, 1, 2, 3`。

> `range` 函数返回一个包含顺序递增的整数列表。

~~~twig
{% for i in range(0, 3) %}
  {{ i }},
{% endfor %}
~~~

来自 `field--node--title.html.twig` 模板的另一个例子:

~~~twig
{% for item in items %}
  {{ item.content }}
{% endfor %}
~~~

在 For 循环中，可以使用一些特殊变量。

| 变量       | 描述|
|---|---|
| items.index     | 当前的循环次数（ 从 1 开始 ）|
| items.index0    | 当前的循环次数（ 从 0 开始 ）|
| items.revindex  | 剩余的循环次数（ 从 1 开始 ） |
| items.revindex0 | 剩余的循环次数（ 从 0 开始 ）|
| items.first     | 是否初次执行|
| items.last      | 是否最后一次执行|
| items.length    | 序列中的元素数量|
| items.parent    | 上级的上下文|

如果循环列表为空，可以利用一个 `else` 语句块来代替输出：

~~~twig
<ul>
{% for user in users %}
  <li>{{ user.username|e }}</li>
{% else %}
  <li><em>查询结果为空</em></li>
{% endfor %}
</ul>
~~~

#### 创建一个 Twig 变量

Sometimes it might be useful to define variables in a template file. `{% set foo="bar" %}` declares a variable `foo` and assigns the value `bar` to it. Later in the template, the variable can be printed out using `{{ foo }}`.

有时候需要在模板中定义变量。`{% set foo="bar" %}` 声明了一个变量 `foo`，并赋值为 `bar`。后面的模板中可以使用`{{ foo }}`来输出。

example.twig.php

---    
~~~twig
{% set foo="bar" %}

# 其他代码

Hi, here's my variable: {{ foo }}
~~~

除了上面的简单变量之外，变量还可以是数组：

another_example.twig.php

---

~~~twig
{%
  set foo_array = [
    'foo',
    'bar',
  ]
%}
~~~