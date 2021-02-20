---
title: 前端菜鸡的自我修养【转载】
date: '2020-06-11T22:12:51.000Z'
tags:
  - 找工作
  - 面试
category:
  - 方法论
---

# 前端菜鸡的自我修养

![image-20200611223251759](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/image-20200611223251759.png)

这是我在Github上看到一个博主分享的学习经验，觉得很有帮助，特地引用过来

[https://github.com/brickspert/blog/issues/16](https://github.com/brickspert/blog/issues/16)

## 正文

先介绍下背景

非211，985本科毕业。一年半PHP经验，一年半前端经验，前端一直在做`React`开发。

半年之前，我是一个前端小小小白。多么小白呢？

1. `css`调样式全靠试。
2. 盒模型，好像知道是啥？好像又不知道！
3. 看到别人说`BFC`，啥是`BFC`？为啥外边距会合并？有些会合并，有些不会合并，这都是啥玩意？
4. `z-index`为啥有时候有效果，有时候没效果？为啥有时候小的值还在大的上面？
5. `js`就会基础使用，稍微复杂的一脸懵逼。
6. 看别人的文章，一看到`prototype`，立马头疼，这都是啥！什么原型，继承，离我远点！
7. 闭包，好像知道是啥。但是说不出来。
8. `arguments`，作用域链等等都是啥？
9. …...

我都不想去思考这些问题，啊，，，头疼，这都是什么？我都不会啊！

这样的我，怎么出去面试？别人随便问个问题，我都不会！

我又去网上看了别人的面试题，娘的哟，这是啥？这又是啥？好像会点，但是说不出来~~

不行不行，我得赶紧学习了。但是我要怎么去准备呢？好像`js，html，css，http`都没系统学过啊？好像`react，webpack`这些玩意也没系统整理过啊。好多啊！

废话不多说，我们开始吧~~

吭哧

吭哧

吭哧

…...

经过半年的准备，我成功面试进了`BAT`！

所以相信自己，从现在开始！你应该比我厉害吧？

我看到很多像我之前一样迷茫的人，我觉得我的经历是可以复制的。就写下来，共勉！

过程分为：

```text
1. 系统学习基础知识
2. 面试题提高
3. 项目
```

## 系统学习基础知识

基础知识通过看书来系统学习。

1. 《JavaScript高级程序设计（第3版）》

   系统学习一遍js，看这本书是非常痛苦的过程。预计时间在2个月左右。

   不要心急，一章一章的过，每个知识点都要去理解，做笔记。

   碰到看不懂的，反复去读，去网上查，一定要搞懂！

2. 《CSS权威指南（第三版）》

   系统学习`css`，预计时间2星期。记得做笔记，不会的点，反复去读，去查。

3. css3教程学习

   这个去网上找份教程，过一遍。每个新属性都去写下。

4. 《html5与css3权威指南》

   这个快速过下前面`html`部分就好了。

   1个星期左右读完。

5. 《图解HTTP》

   非常重要！系统学习`HTTP`。半个月时间~

6. 《ECMAScript 6 入门》

   阮一峰写的。系统学习`ES6`。这个因人而异，时间长短不一，不过真的很重要！

   好了，到这里为止，我们已经系统的学习了前端的各种知识了。应该花费了3个多月了。如果你能坚持下来，绝对会有一个质的飞跃。

## 面试题提高

下面我的策略是，找面试题，把网上能找到的面试都记下来，每个题都去深入研究！

注意，**是深入研究，不是浅显的知道答案就行了**。

面试题大部分来源于这里[https://github.com/h5bp/Front-end-Developer-Interview-Questions/tree/master/Translations/Chinese，还有很多很多其他的面经，我就不一一贴出来了，反正能搜到的我都看了~](https://github.com/h5bp/Front-end-Developer-Interview-Questions/tree/master/Translations/Chinese，还有很多很多其他的面经，我就不一一贴出来了，反正能搜到的我都看了~)

我把我整理的面试题列出来，希望**每个题你都能深入去研究**。

### HTML

1. `DOCTYPE`（文档类型）的作用是什么？

   参考[https://witcher42.github.io/2014/05/28/doctype/](https://witcher42.github.io/2014/05/28/doctype/)

2. 浏览器标准模式 \(`standards mode`\) 、几乎标准模式（`almost standards mode`）和怪异模式 \(`quirks mode`\) 之间的区别是什么？
   * 产生的历史原因是啥？
   * 怪异模式有哪些怪异的行为？
3. 使用 `data-` 属性的好处是什么？

   可以去实践下`data-*`的使用啦

4. 如果把 `HTML5` 看作做一个开放平台，那它的构建模块有哪些？

   研究下`HTML5`的所有模块

5. `cookies`、`sessionStorage` 和`localStorage` 的区别
6. 请解释 `<script>`、`<script async>` 和 `<script defer>` 的区别。
7. 为什么通常推荐将 CSS `<link>` 放置在 `<head></head>` 之间，而将 JS `<script>` 放置在 `</body>` 之前？你知道有哪些例外吗？
8. 什么是渐进式渲染 \(`progressive rendering`\)？
9. `HTML` 和 `XHTML` 有什么区别？
10. `HMTL5`新标签

### CSS

1. `CSS` 中类 \(`class`\) 和`ID` 的区别
2. 请问 "resetting" 和 "normalizing" CSS 之间的区别？你会如何选择，为什么？

   [https://github.com/necolas/normalize.css](https://github.com/necolas/normalize.css)

   [https://github.com/shannonmoeller/reset-css/blob/master/reset.css](https://github.com/shannonmoeller/reset-css/blob/master/reset.css)

3. 请解释浮动 \(`Floats`\) 及其工作原理

   这个非常重要，前面读的书上有这个，一定要完全搞懂。

4. 清除浮动

   重要

5. 描述`z-index`和叠加上下文是如何形成的？

   重要，书上有，先理解。然后我推荐两个文章

   [https://www.w3cplus.com/css/what-no-one-told-you-about-z-index.html](https://www.w3cplus.com/css/what-no-one-told-you-about-z-index.html)

   [http://www.zhangxinxu.com/wordpress/2016/01/understand-css-stacking-context-order-z-index/](http://www.zhangxinxu.com/wordpress/2016/01/understand-css-stacking-context-order-z-index/)

6. 请描述 BFC\(`Block Formatting Context`\) 及其如何工作？

   理解BFC的特性及如何触发BFC

7. CSS sprites

   优点，缺点

8. 图片替换文字方案
9. 你会如何解决特定浏览器的样式问题？
10. 如何为有功能限制的浏览器提供网页？

    渐进增强，优雅降级等等等等

11. 有哪些的隐藏内容的方法？
12. 栅格系统 \(`grid system`\)
13. 你用过媒体查询，或针对移动端的布局`CSS` 吗？
14. 如何优化网页的打印样式？
15. 在书写高效 `CSS` 时会有哪些问题需要考虑？
16. 使用 `CSS` 预处理器的优缺点有哪些？
17. 如果设计中使用了非标准的字体，你该如何去实现？
18. 请解释浏览器是如何判断元素是否匹配某个 `CSS` 选择器？
19. 请描述伪元素 \(`pseudo-elements`\) 及其用途

    伪元素，伪类等等都去研究下

20. 请解释你对盒模型的理解，以及如何在 `CSS` 中告诉浏览器使用不同的盒模型来渲染你的布局
21. 请罗列出你所知道的 `display` 属性的全部值
22. 请解释`inline` 和`inline-block` 的区别
23. 请解释`relative`、`fixed`、`absolute` 和 `static` 元素的区别
24. 请问你有尝试过 `CSS Flexbox` 或者 `Grid` 标准规格吗

    flex很重要，每个属性都要知道。建议去读阮一峰的flex文章

25. 为什么响应式设计 \(`responsive design`\) 和自适应设计 \(`adaptive design`\) 不同？
26. 你有兼容 `retina` 屏幕的经历吗？如果有，在什么地方使用了何种技术？

    移动端开发必须知道！

27. 请问为何要使用 `translate()` 而非 `absolute position`，或反之的理由？为什么？
28. 如果实现一个高性能的`CSS`动画效果？
29. `IFC`
30. `css3`动画

    各种属性熟悉下

31. 布局之：左边定宽，右边自适应
32. 圣杯布局，双飞翼布局
33. 实现垂直居中和水平居中

### Javascript

1. 事件代理
2. 请解释`JavaScript` 中`this` 是如何工作的
3. `javascript`继承

   这个不多说，十分十分重要。建议按照《高程三》的继承那里，仔细理解哦。

4. `javascript`模块化

   理解模块化发展过程，理解 `commonJS`，`AMD`，`CMD`，`ES6`模块化

5. `IIFE` 立即执行函数
6. `null undefined`区别
7. 闭包 与 作用域

   非常重要，书上有！

8. 匿名函数
9. 你是如何组织自己的代码？是使用模块模式，还是使用经典继承的方法？
10. 宿主对象 \(`host objects`\) 和原生对象 \(`native objects`\)
11. 请指出以下代码的区别：`function Person(){}`、`var person = Person()`、`var person = new Person()`？
12. `apply call bind`

    **深入到源码**如何实现这三个功能的。

13. `new`

    源码如何实现的？

14. `document.write()`
15. 特性检测 特性推断 UA字符串嗅探
16. `Ajax`工作原理

    着重理解`XMLHttpRequest`！！

17. 跨域

    图片`ping`,`JSONP`,`CORS`。

    这是面试必问的点。注意一定要完全理解，完全！

18. 变量声明提升
19. 冒泡机制
20. `attribute` 和 `property`
21. `document load` 和 `document DOMContentLoaded`

    非常重要哦

22. `==` 和 `===` 有什么不同
23. 同源策略 \(`same-origin policy`\)

    `Cookie`，`iframe`，`AJAX`同源

24. `strict`模式
25. 为何通常会认为保留网站现有的全局作用域 \(`global scope`\) 不去改变它，是较好的选择
26. 为何你会使用 `load` 之类的事件 \(`event`\)？此事件有缺点吗？你是否知道其他替代品，以及为何使用它们？
27. 请解释什么是单页应用 \(`single page app`\), 以及如何使其对搜索引擎友好 \(`SEO-friendly`\)

    相当重要

28. `Promise`

    怎么用？源码如何实现的？

    推荐文章：[xieranmaya/blog\#3](https://github.com/xieranmaya/blog/issues/3)

29. 使用一种可以编译成 `JavaScript` 的语言来写`JavaScript` 代码有哪些优缺点？
30. `javascript`调试工具
31. 对象遍历 和 数组遍历
32. 可变对象和不可变对象
33. 什么是事件循环 \(`event loop`\)

    非常重要，面试必问。

    深入原理，宏任务，微任务等等

34. `let var const`
35. 数组的方法
36. `web worker`
37. 柯里化
38. 创建对象的三种方法
39. 深拷贝和浅拷贝

    可以实现手写深拷贝

40. 图片懒加载

    咋实现的？

41. 网页各种高度

    这个好难记，我也没记住~

42. 实现页面加载进度条
43. 箭头函数ES5如何实现
    * 箭头函数和普通函数的区别

### React

1. 虚拟`DOM`是啥？以及diff算法原理
2. `react` 事件绑定
3. 生命周期
4. 函数式编程，纯函数
5. `React`创建组件的方式
6. 组件性能优化

   `shuouldComponentUpdate`

   `pureComponent`

   不可变数据

   `key`

   等等优化方法，每一点的优点和缺点

7. 如何设计一个好组件
8. 哪里进行网络请求？为什么
9. 调用`setState`之后发生了什么
10. `refs`
11. `react16`新特性

    尤其理解`time slice`和`suspense`

12. 在 `React` 当中 `Element` 和 `Component` 有何区别
13. 容器组件和展示组件
14. `props.children`
15. 路由实现原理
16. `react`的`setState`同步还是异步？
17. `Redux`，`react-redux`等原理
18. 如何实现异步网络请求的？
19. 组件间通信
20. 高阶组件是什么和常见的高阶组件
21. `React key`是干嘛的？

### webpack

1. `loader`

   自己如何写一个`loader`

2. `plugin`

   自己如何写一个`plugin`

3. `webpack`原理之普通打包
4. `webpack`原理之多文件打包
5. `webpack`原理之提取公共文件
6. `webpack` 如何做到 tree shaking
7. `webpack`配置文件基本概念
8. `webpack`构建流程
9. 前端模块化的理解
10. 打包很慢，怎么解决？
11. 打包出来的文件很大，怎么解决？

### 安全问题

1. `xss`
2. `csrf`
3. 等等....

### HTTP

1. 为什么传统上利用多个域名来提供网站资源会更有效
2. `Long-Polling`、`Websockets` 和 `Server-Sent Event`
3. 常见的请求头和响应头
4. 和缓存有关的`HTTP`首部字段

   相当重要。如何应用的？

5. `HTTP method`
6. `HTTP`状态码
7. `https` 加密过程
8. `http2`新特性

### 性能

1. 你会用什么工具来查找代码中的性能问题？
2. 增强网站的页面滚动效能
3. 重排，重绘，合成

   相当相当重要

4. 合成层

   我在这里理解了一个多星期，静下心来去理解。

   [http://taobaofed.org/blog/2016/04/25/performance-composite/](http://taobaofed.org/blog/2016/04/25/performance-composite/)

5. 前端优化方法
6. `css3`动画和`js`动画对比

### 其他问题

1. 常见排序算法
2. `babel`原理
3. 实现一个幻灯片功能
4. 你最近遇到过什么技术挑战？你是如何解决的？
5. 浏览器输入网址后做了什么？

## 项目

面试问的最多的，除了基础知道，就是项目了。

必须对自己做的项目，有十足的掌握。做项目的时候，有主人翁意识~

项目业务理解，性能优化等等~

行了，到这里就结束了。如果你能坚持下来，我觉得你自己就有很足的自信了！

从一个弱鸡，成长为一个合格的前端菜鸟啦！

路漫漫其修远兮~加油！

一堆胡言乱语，希望对你有帮助。

我再强调一下：基础很重要！项目很重要！

