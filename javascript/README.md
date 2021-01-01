# JavaScript

## 组成

JavaScript由下列三个部分组成

* 核心（ ECMAScript ）
* 文档对象模型（ DOM ）
* 浏览器对象模型（ BOM ）

![image-20200610211629279](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/image-20200610211629279.png)

## ECMAScript

ECMAScript是由网景的布兰登·艾克开发的一种脚本语言的标准化规范；最初命名为Mocha，后来改名为LiveScript，最后重命名为JavaScript。1995年12月，升阳与网景联合发表了JavaScript。1996年11月，网景公司将JavaScript提交给欧洲计算机制造商协会进行标准化。ECMA-262的第一个版本于1997年6月被Ecma组织采纳。ECMA Script是ECMA-262标准化的脚本语言的名称。尽管JavaScript和JScript与ECMAScript兼容，但包含超出ECMA Script的功能。

由 ECMA定义的 ECMAScript 与 Web 浏览器没有依赖关系。实际上，这门语言本身并不包含输入和输出定义。ECMA定义的只是这门语言的基础，而在此基础之上可以构建更完善的脚本语言。我们常见的 Web 浏览器只是 ECMAScript 实现可能的宿主环境之一。宿主环境不仅提供基本的 ECMAScript 实现，同时也会提供该语言的扩展，以便语言与环境之间对接交互。而这些扩展——如 DOM，则利用 ECMAScript 的核心类型和语法提供更多更具体的功能，以便实现针对环境的操作。其他 宿主环境包括 Node\(一种服务端 JavaScript 平台\)和 Adobe Flash。

ECMA规定了JavaScript的下列组成部分

* 语法
* 类型
* 句子
* 关键字
* 保留字
* 操作符
* 对象

## 文档对象模型\(DOM\)

文档对象模型\(DOM，Document Object Model\)是针对 XML 但经过扩展用于 HTML 的应用程序编程接口\(API，Application Programming Interface\)。DOM 把整个页面映射为一个多层节点结构。HTML 或 XML 页面中的每个组成部分都是某种类型的节点，这些节点又包含着不同类型的数据。

DOM树的**结构**长这样

![image-20200610210642648](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/image-20200610210642648.png)

为什么要构建 DOM 树呢？这是因为浏览器无法直接理解和使用 HTML，所以需要将 HTML 转换为浏览器能够理解的结构——DOM 树。

![img](https://img-1251598303.cos.ap-guangzhou.myqcloud.com/125849ec56a3ea98d4b476c66c754f79.png)

通过 DOM 创建的这个表示文档的树形图，开发人员获得了控制页面内容和结构的主动权。借助 DOM 提供的 API，开发人员可以轻松自如地删除、添加、替换或修改任何节点。

## 浏览器对象模型（ BOM ）

Internet Explorer 3 和 Netscape Navigator 3 有一个共同的特色，那就是支持可以访问和操作浏览器窗口的浏览器对象模型\(BOM，Browser Object Model\)。开发人员使用 BOM 可以控制浏览器显示的页面 以外的部分。而 BOM 真正与众不同的地方\(也是经常会导致问题的地方\)，还是它作为 JavaScript 实现 的一部分但却没有相关的标准。这个问题在 HTML5 中得到了解决，HTML5 致力于把很多 BOM 功能写 入正式规范。HTML5 发布后，很多关于 BOM 的困惑烟消云散。

从根本上讲，BOM 只处理浏览器窗口和框架;但人们习惯上也把所有针对浏览器的 JavaScript 扩展 算作 BOM 的一部分。下面就是一些这样的扩展:

* 弹出新浏览器窗口的功能;
* 移动、缩放和关闭浏览器窗口的功能;
* 提供浏览器详细信息的 navigator 对象;
* 提供浏览器所加载页面的详细信息的 location 对象;
* 提供用户显示器分辨率详细信息的 screen 对象;
* 对 cookies 的支持;
* 像 XMLHttpRequest 和 IE 的 ActiveXObject 这样的自定义对象。

## 总结

1. DOM是文档对象模型,是将 html 转换成计算机能够读懂后的 DOM 树，我们可以通过 DOM 提供的 api 以实现对页面样式、大小的调整
2. BOM是浏览器对象模型,用来获取或设置浏览器的属性、行为,例如：新建窗口、获取屏幕分辨率、浏览器版本号等

