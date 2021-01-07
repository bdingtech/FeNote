---
description: 在 CSS 中，所有的元素都被一个个的“盒子（box）”包围着，理解这些“盒子”的基本原理，是我们使用CSS实现准确布局、处理元素排列的关键。
---

# 盒模型那些事

## 块级元素和内联元素

块级元素

* 盒子会在内联的方向上扩展并占据父容器在该方向上的所有可用空间，在绝大数情况下意味着盒子会和父容器一样宽
* 每个盒子都会换行
* [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 和 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) 属性可以发挥作用
* 内边距（padding）, 外边距（margin） 和 边框（border） 会将其他元素从当前盒子周围“推开”

block元素（块元素）大致有：P\|H1\|H2\|H3\|H4\|H5\|H6\|UL\|OL\|PRE\| DL \| DIV \| NOSCRIPT \| BLOCKQUOTE \| FORM \| HR \| TABLE \| FIELDSET \| ADDRESS\(随着html5标准的推进，一些元素将被废除，而一些新的元素将被引入\)注意的是并非所有的block元素的默认display属性都是block，像table这种display:table的元素也是block元素。

内联元素

* 盒子不会产生换行。
*  [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 和 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height) 属性将不起作用。
* **垂直方向的内边距、外边距以及边框会被应用但是不会把其他处于 `inline` 状态的盒子推开。**
* 水平方向的内边距、外边距以及边框会被应用且会把其他处于 `inline` 状态的盒子推开。

inline元素（内联元素）大致有：\| TT \| I \| B \| BIG \| SMALL\|EM \| STRONG \| DFN \| CODE \|SAMP \| KBD \| VAR \| CITE \| ABBR \| ACRONYM\|A \| IMG \| OBJECT \| BR \| SCRIPT \| MAP \| Q \| SUB \| SUP \| SPAN \| BDO\|INPUT \| SELECT \| TEXTAREA \| LABEL \| BUTTON

{% hint style="info" %}
注意：替换元素设置的padding是生效的，并且撑开了父元素。对于非替换 inline元素，设置垂直方向的margin是无效的，设置垂直方向的padding虽然元素的内容范围是增大了，不过只是表象，对周围元素无任何影响。
{% endhint %}

```text
置换元素
置换元素是指：浏览器根据元素的标签和属性，来决定元素的具体显示内容。

例如：浏览器根据<img>标签的src属性显示图片。根据标签的type属性决定显示输入框还是按钮。
置换元素在其显示中生成了框，这也就是有的内联元素能够设置宽高的原因。
html中的<img><input><textarea><select><object>都是置换元素，这些置换元素往往没有实际内容，即是一个空元素。


非置换元素
浏览器中的大多数元素都是不可置换元素，即其内容直接展示给浏览器。

例如<label>标签，<p>标签里的内容会被浏览器直接显示给用户。

```

> 引用：[inline元素与padding margin的爱恨情仇](https://www.jianshu.com/p/d44142161eb7)

## CSS 盒模型

### [标准盒模型](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/The_box_model#%E6%A0%87%E5%87%86%E7%9B%92%E6%A8%A1%E5%9E%8B)

在标准模型中，如果你给盒设置 `width` 和 `height`，实际设置的是 _content box_。 padding 和 border 再加上设置的宽高一起决定整个盒子的大小。 见下图。

假设定义了 `width`, `height`, `margin`, `border`, and `padding`:

```markup
.box {
  width: 350px;
  height: 150px;
  margin: 25px;
  padding: 25px;
  border: 5px solid black;
}
```

如果使用标准模型宽度 = 410px \(350 + 25 + 25 + 5 + 5\)，高度 = 210px \(150 + 25 + 25 + 5 + 5\)，padding 加 border 再加 content box。

![](../.gitbook/assets/image%20%2820%29.png)

### IE盒模型

你可能会认为盒子的大小还要加上边框和内边距，这样很麻烦，而且你的想法是对的! 因为这个原因，css还有一个替代盒模型。使用这个模型，所有宽度都是可见宽度，所以内容宽度是该宽度减去边框和填充部分。使用上面相同的样式得到 \(width = 350px, height = 150px\).

![Showing the size of the box when the alternate box model is being used.](https://mdn.mozillademos.org/files/16557/alternate-box-model.png)

默认浏览器会使用标准模型。如果需要使用替代模型，您可以通过为其设置 `box-sizing: border-box` 来实现。 这样就可以告诉浏览器使用 `border-box` 来定义区域，从而设定您想要的大小。

```text
.box {
  box-sizing: border-box;
} 
```

如果你希望所有元素都使用替代模式，而且确实很常用，设置 `box-sizing` 在 `<html>` 元素上，然后设置所有元素继承该属性，正如下面的例子。如果想要深入理解，请看 [the CSS Tricks article on box-sizing](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)。

```text
html {
  box-sizing: border-box;
}
*, *::before, *::after {
  box-sizing: inherit;
}
```

