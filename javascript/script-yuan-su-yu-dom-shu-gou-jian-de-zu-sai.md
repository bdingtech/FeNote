---
title: JS高程-Script元素与DOM树构建的阻塞
date: '2020-06-11T11:08:24.000Z'
category:
  - 前端
tags:
  - JavaScript
---

# script 元素与 DOM 数构建的阻塞

## script元素

### 属性

向 HTML 页面中插入 JavaScript 的主要方法，就是使用 script 元素。这个元素由 Netscape 创造 并在 Netscape Navigator 2 中首先实现。后来，这个元素被加入到正式的 HTML 规范中。HTML 4.01 为 script 定义了下列 6 个属性。

![image-20200611111047304](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/image-20200611111047304.png)

### **noscript**元素

早期浏览器都面临一个特殊的问题，即当浏览器不支持 JavaScript 时如何让页面平稳地退化。对这 个问题的最终解决方案就是创造一个 noscript 元素，用以在不支持 JavaScript 的浏览器中显示替代 的内容。这个元素可以包含能够出现在文档 body 中的任何 HTML 元素—— script 元素除外。包含 在 noscript 元素中的内容只有在下列情况下才会显示出来:

* 浏览器不支持脚本
* 浏览器支持脚本，但脚本被禁用

符合上述任何一个条件，浏览器都会显示 noscript 中的内容。而在除此之外的其他情况下，浏览器不会呈现 noscript 中的内容。

```markup
<html>
  <head>
    <title>Example HTML Page</title>
    <script type="text/javascript" defer="defer" src="example1.js"></script> 
    <script type="text/javascript" defer="defer" src="example2.js"></script>
  </head>
  <body>
    <noscript> 
      <p>本页面需要浏览器支持(启用)JavaScript。</p>
    </noscript> 
  </body>
</html>
```

这个页面会在脚本无效的情况下向用户显示一条消息。而在启用了脚本的浏览器中，用户永远也不 会看到它——尽管它是页面的一部分。

## 文档模式

在多年以前（IE6诞生以前），各浏览器都处于各自比较封闭的发展中（基本没有兼容性可谈）。随着WEB的发展，兼容性问题的解决越来越显得迫切，随即，各浏览器厂商发布了按照**标准模式**（遵循各厂商制定的统一标准）工作的浏览器，比如IE6就是其中之一。

但是考虑到以前建设的网站并不支持标准模式，所以各浏览器在加入标准模式的同时也保留了**混杂模式**（即以前那种未按照统一标准工作的模式，也叫怪异模式）。

## script与DOM树构建的阻塞

什么是DOM树我们已近在上一期《 JS高程-JavaScript的组成 》中介绍过了，以后可能还会开一期详细介绍，现在我们来看看DOM树是如何生成的

### DOM树是如何生成的

在渲染引擎内部，有一个叫 HTML 解析器（HTMLParser）的模块，它的职责就是负责将 HTML 字节流转换为 DOM 结构。所以这里我们需要先要搞清楚 HTML 解析器是怎么工作的。

![img](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/1bfcd419acf6402c20ffc1a5b1909d8c.png)

#### 第一个阶段  通过分词器将字节流转换为 Token。

V8 编译 JavaScript 过程中的第一步是做词法分析，将 JavaScript 先分解为一个个 Token。解析 HTML 也是一样的，需要通过分词器先将字节流转换为一个个 Token，分为 Tag Token 和文本 Token。上述 HTML 代码通过词法分析生成的 Token 如下所示：

![image-20200611135850372](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/image-20200611135850372.png)

![img](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/b16d2fbb77e12e376ac0d7edec20ceac.png)

#### 第二个阶段 将Token解析为 DOM 节点并将 DOM 节点添加到DOM树中

HTML 解析器维护了一个 Token 栈结构，该 Token 栈主要用来计算节点之间的父子关系，在第一个阶段中生成的 Token 会被按照顺序压到这个栈中。具体的处理规则如下所示：

* 如果压入到栈中的是 StartTag Token，HTML 解析器会为该 Token 创建一个 DOM 节点，然后将该节点加入到 DOM 树中，它的父节点就是栈中相邻的那个元素生成的节点。
* 如果分词器解析出来是文本 Token，那么会生成一个文本节点，然后将该节点加入到 DOM 树中，文本 Token 是不需要压入到栈中，它的父节点就是当前栈顶 Token 所对应的 DOM 节点。
* 如果分词器解析出来的是 EndTag 标签，比如是 EndTag div，HTML 解析器会查看 Token 栈顶的元素是否是 StarTag div，如果是，就将 StartTag div 从栈中弹出，表示该 div 元素解析完成。

为了更加直观地理解整个过程，下面我们结合一段 HTML 代码（如下），来一步步分析 DOM 树的生成过程。

```markup
<html>
<body>
    <div>1</div>
    <div>test</div>
</body>
</html>
```

解析出第一个文本 Token 时的状态

![img](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/dc0ddd4e3bf3569555f4b1ebec7a8caf.png)

再接下来，分词器解析出来第一个 EndTag div，这时候 HTML 解析器会去判断当前栈顶的元素是否是 StartTag div，如果是则从栈顶弹出 StartTag div，如下图所示：

![img](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/c4a255a8881ef9d21e419aa010ce24a6.png)

按照同样的规则，一路解析，最终结果如下图所示：

![img](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/aabf14cde38b058c5203195db82ec22e.png)

通过不断的进栈与出栈，完成了对HTML的词法分析，生成了DOM树，在实际场景中还会涉及到图片、音频、视频等文件，所以处理过程比上面的这个DEMO要复杂很多。

### JavaScript 是如何影响 DOM 生成的

要想知道JavaScript 是如何影响 DOM 生成的，首先我们得先来了解两个 script 标签的两个属性，`defer`、`async`。

#### defer

&lt;script&gt; 标签定义了 defer 属性。这个属性的用途是表明脚本在执行时不会影响页面的构造。也就是说，**脚本会被延迟到整个页面都解析完毕后再运行**。因此，在 &lt;script&gt; 元素中设置 defer 属性，相当于告诉浏览器**立即下载，但延迟执行**。

```markup
<!DOCTYPE html>
<html>
    <head>
        <title>Example HTML Page</title>
        <!--使用了defer之后，即使是在head中引用的script，也将在浏览器解析完DOM树之后执行-->
        <script type="text/javascript" defer="defer" src="example1.js"></script> 
      <script type="text/javascript" defer="defer" src="example2.js"></script>
    </head>
  <body>
            <!-- 这里放内容 --> 
  </body>
</html>
```

在这个例子中，虽然我们把 script 元素放在了文档的 head 元素中，但其中包含的脚本将延迟 到浏览器到/html标签后再执行。HTML5 规范要求脚本按照它们出现的先后顺序执行，因此第一个延迟脚本会先于第二个延迟脚本执行，而这两个脚本会先于 DOMContentLoaded 事件 执行。在现实当中，延迟脚本并不一定会按照顺序执行，也不一定会在 DOMContentLoaded 事件触发前执行，因此最好只包含一个延迟脚本。

#### async

HTML5 为 &lt;script&gt; 元素定义了 async 属性。这个属性与 defer 属性类似，都用于改变处理脚本的行为。同样与defer类似，async只适用于外部脚本文件，并告诉浏览器立即下载文件。但与defer不同的是，标记为 async 的脚本并不保证按照指定它们的先后顺序执行。**指定 async 属性的目的是不让页面等待两个脚本下载和执行，从而异步加载页面其他内容。 为此，建议异步脚本不要在加载期间修改 DOM。**

```markup
<!DOCTYPE html>
<html>
<head>
    <title>Example HTML Page</title>
   <!--与defer不同的是，下载完成之后就会立即执行，而不会等待dom解析完毕-->
    <script type="text/javascript" async src="example1.js"></script>
  <script type="text/javascript" async src="example2.js"></script>
</head>
 <body>
            <!-- 这里放内容 --> 
  </body>
</html>
```

async 和 defer 虽然都是异步的（ 因为 **JavaScript 文件的下载过程会阻塞 DOM 解析** ），不过还有一些差异，使用 async 标志的脚本文件一旦加载完成，会立即执行；而使用了 defer 标记的脚本文件，会在 DOMContentLoaded 事件之前执行。

#### JavaScript会阻塞DOM生成

我们再来看看稍微复杂点的 HTML 文件，如下所示：

```markup
<html>
<body>
    <div>1</div>
    <script>
    let div1 = document.getElementsByTagName('div')[0]
    div1.innerText = 'time.geekbang'
    </script>
    <div>test</div>
</body>
</html>
```

我在两段 div 中间插入了一段 JavaScript 脚本，这段脚本的解析过程就有点不一样了。 script 标签之前，所有的解析流程还是和之前介绍的一样，但是解析到 script 标签时，渲染引擎判断这是一段脚本，此时 HTML 解析器就会暂停 DOM 的解析，因为接下来的 JavaScript 可能要修改当前已经生成的 DOM 结构。

> 这时要等script中的脚本执行完，DOM 才会继续解析，就阻塞了

但是如果我们是从外部引入JS文件呢，毕竟这种情况比较常见

```markup
<html>
<body>
    <div>1</div>
    <!--当浏览器解析到这里时，会去下载foo.js，所以会阻塞DOM解析-->
    <script type="text/javascript" src='foo.js'></script>
    <div>test</div>
</body>
</html>
```

这段代码的功能还是和前面那段代码是一样的，不过这里我把内嵌 JavaScript 脚本修改成了通过 JavaScript 文件加载。其整个执行流程还是一样的，执行到 JavaScript 标签时，暂停整个 DOM 的解析，执行 JavaScript 代码，不过这里执行 JavaScript 时，需要先下载这段 JavaScript 代码。这里需要重点关注下载环境，因为 JavaScript 文件的下载过程会阻塞 DOM 解析，而通常下载又是非常耗时的，会受到网络环境、JavaScript 文件大小等因素的影响。

不过 Chrome 浏览器做了很多优化，其中一个主要的优化是预解析操作。当渲染引擎收到字节流之后，会开启一个预解析线程，用来分析 HTML 文件中包含的 JavaScript、CSS 等相关文件，解析到相关文件之后，预解析线程会提前下载这些文件。

再回到 DOM 解析上，我们知道引入 JavaScript 线程会阻塞 DOM，不过也有一些相关的策略来规避，比如使用 CDN 来加速 JavaScript 文件的加载，压缩 JavaScript 文件的体积。另外，如果 JavaScript 文件中没有操作 DOM 相关代码，就可以将该 JavaScript 脚本设置为**异步加载**，通过 async 或 defer 来标记代码，使用方式如下所示：

```markup
 <script async type="text/javascript" src='foo.js'></script>
```

```markup
<script defer type="text/javascript" src='foo.js'></script>
```

## 总结

1. `async`和`defer`都是异步的，只是执行的时机不同
2. async 和 defer 的优点是异步加载，不会阻塞DOM的解析，但是不能在解析DOM的过程中就操作DOM，多一如果JavaScript文件中没有操作DOM的相关的代码，就可以将JavaScript脚本设置为异步加载，加快网页渲染速度

