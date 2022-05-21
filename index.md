title: Markdown 教学
speaker: MSC
css: 
    - https://fonts.googleapis.com/css2?family=Ubuntu:wght@400;600&family=Source+Code+Pro&family=JetBrains+Mono:ital,wght@0,300;0,400;0,600;0,700;1,400;1,700
    - https://fastly.jsdelivr.net/npm/lxgw-wenkai-webfont@1.1.0/style.css
    - https://fastly.jsdelivr.net/npm/lxgw-wenkai-screen-webfont@1.1.0/style.css
    - style.css
plugins:
    - echarts

<slide :class="aligncenter size-70">
<link rel="stylesheet" href="style.css">

# Markdown 教学 {.text-shadow}

---

By 王鹤翔（MSC） {.text-intro}

[:fa-github: Github](https://github.com/TonyCrane/MarkdownLecture){.button.ghost}

<slide :class="size-60">

# 什么是 markdown

---

:::shadowbox

轻量级文本标记语言（markup language）

---

纯文本编写带格式文档

---

可以转为 HTML（映射到 HTML 的子集）

---

方便、简单、用途多

:::

<slide :class="size-70">

:::{.content-left}

# 历史

---

- 2004 年 John Gruber 发布了第一个 markdown 语法手册和 perl 语言写的转换器
- 以易读易写为目标，成为电子邮件标记格式惯例
- 2016 年正式注册了 CommonMark（标准化）、GFM（GitHub 风格）等变体
- ……


:::

:::{.content-right}
<br/>
<br/>
> Markdown is intended to be as easy-to-read and easy-to-write as is feasible.
> ==John Gruber==
{.text-quote}

<slide :class="size-50">

# 语法

---

- John Gruber 的 markdown 语法，简单直接，但不细致
    - [daringfireball.net/projects/markdown](https://daringfireball.net/projects/markdown)
- CommonMark 标准，明确细节
    - [spec.commonmark.org](https://spec.commonmark.org/0.30/)
- 各个网站、软件有自己的语法标准、扩展语法
    - GitHub GFM 标准 [github.github.com/gfm](https://github.github.com/gfm/)（改自 CommonMark）
    - Typora [support.typora.io](https://support.typora.io/)（改自 CommonMark）
    - Pandoc 标准 [pandoc.org/MANUAL.html](https://pandoc.org/MANUAL.html#pandocs-markdown)
    - ……

<slide :class="size-60">

# 常用软件

---

- Typora，经典流行，但付费，语法改自 CommonMark 标准 
    - [typora.io](https://typora.io/)
- MarkText，新兴编辑器，开源，支持 CommonMark、GFM、部分 Pandoc 
    - [:fa-github: marktext/marktext](https://github.com/marktext/marktext)
- VSCode，自带预览，可以通过插件达到更好效果
    - [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
    - [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)（推荐）
- notion、幕布、飞书等笔记软件
- ……

<slide :class="size-60 aligncenter">

# 语法讲解

---

<slide :class="size-60">

:::{.content-left}

# 标题

---

- 井号 # 开头，后接内容
- 井号与标题间至少一个空格
- 只有 1～6 级标题，7 及以上不会变成标题格式
- 转为 html 利用 h1 ~ h6 tag
- 内容后面可以接任意多 # 来 ”闭合“
- 可以跨过某一级，但请明确好层级关系

:::

:::{.content-right}
```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
```html
<h1>一级标题</h1>
<h2>二级标题</h2>
<h3>三级标题</h3>
<h4>四级标题</h4>
<h5>五级标题</h5>
<h6>六级标题</h6>
```

<slide :class="size-60">

:::{.content-left}

# *标题（Setext）

---

- 使用 # 的称为 ATX 样式
- markdown 支持另一种称为 Setext 样式的标题
- 文字下方加任意多 = 表示一级标题
- 文字下方加任意多 - 表示二级标题

:::

:::{.content-right}
```markdown
一级标题
=======

二级标题
-------
```
```html
<h1>一级标题</h1>
<h2>二级标题</h2>
```

<slide :class="size-60">

:::{.content-left}

# 引言

---

- 一个 > 加一个空格后接内容
- 内部可以嵌套使用 markdown 语法
    - 可以嵌套任意多层引言
- 连续的 > 行属于同一个引言块
- 需要一个空行来退出环境
- 软件里一般使用一次 enter 退出一层

:::

:::{.content-right}
```markdown
> ## Quote
> 第二行
> > 第二层
> 
> 回到第一层

退出引言
```

<slide :class="size-60">

:::{.content-left}

# 无序列表

---

- `- + *` 后接一个空格然后接内容
- 同一个层级的符号要相同
- 如果一个项中要包含内容，需要换一行然后加一次缩进
- 嵌套列表直接缩进一次即可

:::

:::{.content-right}
```markdown
- node 1
- node 2

  content in node 2
- node 3

* 第一层
    + 第二层
        * 第三层
    + 第二层
* 第一层
```

<slide :class="size-60">

:::{.content-left}

# 有序列表

---

- 数字加点 后接空格 再接内容
    - 也可以数字加 ) 后接空格 再接内容
- 标准的 md 完全无视数字内容，所有有序列表都从 1 开始计数
- 但一般软件都会处理起始数字
- 有序列表可以和无序列表互相嵌套

:::

:::{.content-right}
```markdown
1. node 1
2. node 2
4. node 3
1. node 4

1. 有序 
    - 嵌套无序
    - 嵌套无序
2. 有序
```

<slide :class="size-60">

:::{.content-left}

# 分割线

---

- 使用 `* - _` 中任意一个字符重复至少三次
- 可以有空格分隔，甚至组织成不同样式
- 被转换为 html 中的 \<hr/>
- 分割线上下最好都加空行
- 特别记住 - 分割线上方不要有文字（Setext 标题）

:::

:::{.content-right}
```text
***

---

___

* * *
_  __  _  __

----------------
```

<slide :class="size-60">

:::{.content-left}

# 代码块

---

- 空行加一个缩进创建一个代码块
- 被转为 html 中 \<pre>\<code>...\</code>\</pre>
- 内部被原样展现
- 软件不会进行代码高亮

:::

:::{.content-right}
```markdown
code block:

    print("hello world")
    # line 2

out
```

<slide :class="size-60">

:::{.content-left}

# 代码块

---

- 使用三个或以上 ` 或 ~ 围起来构成代码块
- ` 或 ~ 后面可以加语言名称
    - 带有高亮支持的软件会对其进行高亮显示
    - 不加（或加 text）不进行高亮

:::

:::{.content-right}
~~~markdown
```c
#include <stdio.h>

int main() {
    printf("hello world\n");
    return 0;
}
```
~~~

<slide :class="size-60">

:::{.content-left}

# 行内标记

---

- 格式见右侧，* 和 _ 等效
- 下划线无 markdown 语法，可以直接使用 html 的 \<u> tag 来实现
- 行内标记都可以互相嵌套
    - 也可以嵌套在其它块中
    - 行内代码中不行
- 最好在标记左右均加空格
- 文字中使用 * 建议加上 \ 转义

:::

:::{.content-right}
```markdown
*斜体* _也是斜体_ \*这不是斜体\*
**粗体** __也是粗体__
***粗斜体*** ___也是粗斜体___
`行内代码`
~~删除线~~
<u>下划线</u>
```
```html
<em>斜体</em>
<strong>粗体</strong>
<code>行内代码</code>
<del>删除线</del>
```

<slide :class="size-60">

:::{.content-left}

# 图片

---

- 感叹号-方括号-圆括号结合的形式
- 图片名可以省略
- 位置可以是链接，也可以是本地文件路径
- md 语法插入图片无法调大小，使用 html img 的 style 可以调节
- 软件一般可以帮你保存图片到某一目录
- 记住图片不会嵌入 md 文件中，要交给别人 md 文件的话请附带上所有素材文件

:::

:::{.content-right}
```markdown
![图片名](图片位置)
![](图片位置)
<img src="图片位置" alt="图片名" 
    style="..."/>
```

<slide :class="size-60">

:::{.content-left}

# 链接

---

- 方括号-圆括号组合
- 文字是要显示的内容，链接附加在其上
- 文字中可以嵌套行内标记格式

:::

:::{.content-right}
```markdown
[文字](链接)
```
```html
<a href="链接">文字</a>
```

<slide :class="size-50">

# 内连 HTML

---

- markdown 中一般可以直接使用 html 语法和 css 样式
- 解析器会原封不动的保留 html 内容
- 文本中使用 \<tag\> 这样的字样需要用 \ 转义
- GitHub（GFM）仅支持少量 html，且不支持 css 样式
- html 语法不赘述

<slide :class="size-60">

:::{.content-left}

# 表格

---

- 不在标准中，但一般这样使用
- 每个单元格的内容用 | 分开
    - 内容中使用 | 要用 \ 转义
- 第二行一定要有，规定整列对齐方式
    - `|--|` 或 `|:--|` 左对齐
    - `|--:|` 右对齐
    - `|:--:|` 居中对齐
    - `-` 的个数随意
- 仅可以处理简单表格，复杂的用 html 插入
- 推荐 [tablesgenerator.com](https://www.tablesgenerator.com/)

:::

:::{.content-right}
```markdown
|表头|表头|表头|
|:--|:--:|--:|
|居左|居中|居右|
|...|...|...|
```
|表头|表头|表头|
|:--|:--:|--:|
|居左|居中|居右|
|...|...|...|

<slide :class="size-50">

# 更细致的文档？

---

- CommonMark 标准：[spec.commonmark.org](https://spec.commonmark.org/0.30)
- 对应软件、解析器的文档
- ~~没啥好看的，能用就行~~

<slide :class="size-60">

:::{.content-left}

# 有什么用？

---

- 写 README、写文档
- 写笔记、写实验报告、写论文
- 写网站内容
    - 博客：hexo
    - 文档：mkdocs
- 甚至写这个幻灯片

:::

:::{.content-right}

# 怎么能更好看？

---

- 自己写 css 样式
- 找别人写好的样式
    - 仿 LaTeX typora 主题：<br/>[:fa-github: Keldos-Li/typora-latex-theme](https://github.com/Keldos-Li/typora-latex-theme)
    - GitHub 上有很多各种软件的主题

<slide :class="size-60 aligncenter">

# 结{.text-shadow}

---

Thanks for watching{.text-landing}

学习愉快(￣▽￣)