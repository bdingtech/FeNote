---
description: >-
  HTML5 是对 HTML 标准的第五次修订。其主要的目标是将互联网语义化，以便更好地被人类和机器阅读，并同时提供更好地支持各种媒体的嵌入。HTML5
  的语法是向后兼容的。现在国内普遍说的 H5 是包括了 CSS3，JavaScript
  的说法（严格意义上说，这么叫并不合适，但是已经这么叫开了，就将错就错了）。
---

# HTML5新增内容



![](../.gitbook/assets/image%20%2818%29.png)

## **语义：**新增语义化标签

以前制作网页布局时基本使用div来做。div就是一个普通的块级标签，**对于搜索引擎来说，是没有语义的，所以说这个改进主要是针对浏览器而言**

###  **新增内容**

* &lt;header&gt;: 头部标签
* &lt;nav&gt;：导航标签
* &lt;main&gt;：主体标签
* &lt;article&gt;：独立的内容标签
* &lt;section&gt;：区段标签
* &lt;aside&gt;：侧边栏标签
* &lt;footer&gt;：尾部标签

![](../.gitbook/assets/image%20%2819%29.png)

###  带来的好处

1. 在没有CSS的情况下，页面也能呈现出很好地内容结构、代码结构
2. 有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重
3. 方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页
4. 便于团队开发和维护，语义化更具可读性，是下一步吧网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化。

## **多媒体：**新增多媒体标签

使 video 和 audio 成为了在所有 Web 中的一等公民。

以前想在网页中插入音视频得用到 Flash ，而 Flash 因为许多漏洞，导致可能出现安全问题，已逐渐被各大浏览器厂商淘汰

###  **新增内容**

 新增视频标签 `<video>`

 新增音频标签 `<audio>`

##  **设备访问 Device Access：**新增表单类型和属性

###  新增内容

####  属性

`autocomplete`：自动完成，适用于 `<form>` 标签，以及以下类型的 `<input>` 标签：text, search, url, telephone, email, password, datepickers, range, color。用法：`<form autocomplete="on“></form>`或者单独在input中用off

`autofocus`：自动地获得焦点，适用于所有 `<input>` 标签的类型用法：`<input autofocus="autofocus" />`

`multiple`：可选择多个值，适用于`<input>`中type为email和file用法：`<input type="file" multiple="multiple" />`

`placeholder`：适用于`<input>`中type为：text, search, url, telephone, email, password

`required`：规定不能为空，适用于以下类型的 `<input>` 标签：text, search, url, telephone, email, password, date picke

####  类型

![](../.gitbook/assets/image%20%2817%29.png)

 更多详情请查看 MDN [https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/Input](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/Input)

## **连通性**

能够让你和服务器之间通过创新的新技术方法进行通信。

### **新增内容**

[Web Sockets](https://developer.mozilla.org/zh-CN/docs/WebSockets)

允许在页面和服务器之间建立持久连接并通过这种方法来交换非 HTML 数据。

[Server-sent events](https://developer.mozilla.org/zh-CN/docs/Server-sent_events/Using_server-sent_events)

允许服务器向客户端推送事件，而不是仅在响应客户端请求时服务器才能发送数据的传统范式。

[WebRTC](https://developer.mozilla.org/zh-CN/docs/WebRTC)

这项技术，其中的 RTC 代表的是即时通信，允许连接到其他人，直接在浏览器中控制视频会议，而不需要一个插件或是外部的应用程序。

## 离线 & 存储

能够让网页在客户端本地存储数据以及更高效地离线运行。

### **新增内容**

[IndexedDB](https://developer.mozilla.org/zh-CN/docs/IndexedDB)

是一个为了能够在浏览器中存储大量结构化数据，并且能够在这些数据上使用索引进行高性能检索的 Web 标准。

\*\*\*\*[**localstorage**](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/localStorage)\*\*\*\*

没有时间限制的数据存储

[sessionStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage)

针对一个 session 的数据存储, 当用户关闭浏览器窗口后，数据会被删除。

## 3D, 图像 & 效果

### 新增内容

 [Canvas ](https://developer.mozilla.org/zh-CN/docs/Canvas_tutorial)

 [WebGL](https://developer.mozilla.org/zh-CN/docs/WebGL)

 [SVG](https://developer.mozilla.org/zh-CN/docs/SVG)

## 设备访问

[使用 Camera API](https://developer.mozilla.org/zh-CN/docs/DOM/Using_the_Camera_API)允许使用和操作计算机的摄像头，并从中存取照片。

[触控事件](https://developer.mozilla.org/zh-CN/docs/DOM/Touch_events)对用户按下触控屏的事件做出反应的处理程序。

[使用地理位置定位](https://developer.mozilla.org/zh-CN/docs/WebAPI/Using_geolocation)让浏览器使用地理位置服务定位用户的位置。

[检测设备方向](https://developer.mozilla.org/zh-CN/docs/Detecting_device_orientation)让用户在运行浏览器的设备变更方向时能够得到信息。这可以被用作一种输入设备（例如制作能够对设备位置做出反应的游戏）或者使页面的布局跟屏幕的方向相适应（横向或纵向）。

[指针锁定 API](https://developer.mozilla.org/zh-CN/docs/API/Pointer_Lock_API)允许锁定到内容的指针，这样游戏或者类似的应用程序在指针到达窗口限制时也不会失去焦点。

##  性能&集成

[Web Workers](https://developer.mozilla.org/zh-CN/docs/DOM/Using_web_workers)能够把 JavaScript 计算委托给后台线程，通过允许这些活动以防止使交互型事件变得缓慢。

[`XMLHttpRequest`](https://developer.mozilla.org/zh-CN/docs/DOM/XMLHttpRequest) Level 2允许异步读取页面的某些部分，允许其显示动态内容，根据时间和用户行为而有所不同。这是在 [Ajax](https://developer.mozilla.org/zh-CN/docs/AJAX)背后的技术。即时编译的 JavaScript 引擎新一代的 JavaScript 引擎功能更强大，性能更杰出。

[History API](https://developer.mozilla.org/zh-CN/docs/DOM/Manipulating_the_browser_history)允许对浏览器历史记录进行操作。这对于那些交互地加载新信息的页面尤其有用。

[contentEditable 属性：把你的网站改变成 wiki !](https://developer.mozilla.org/zh-CN/docs/HTML/Content_Editable)HTML5 已经把 contentEditable 属性标准化了。了解更多关于这个特性的内容。

[拖放](https://developer.mozilla.org/zh-CN/docs/DragDrop/Drag_and_Drop)HTML5 的拖放 API 能够支持在网站内部和网站之间拖放项目。同时也提供了一个更简单的供扩展和基于 Mozilla 的应用程序使用的 API。

[HTML 中的焦点管理](https://developer.mozilla.org/zh-CN/docs/HTML/Focus_management_in_HTML)支持新的 HTML5 `activeElement` 和 `hasFocus` 属性。

[基于 Web 的协议处理程序](https://developer.mozilla.org/zh-CN/docs/Web-based_protocol_handlers)你现在可以使用 `navigator.registerProtocolHandler()` 方法把 web 应用程序注册成一个协议处理程序。

[`requestAnimationFrame`](https://developer.mozilla.org/zh-CN/docs/DOM/window.requestAnimationFrame)允许控制动画渲染以获得更优性能。

[全屏 API](https://developer.mozilla.org/zh-CN/docs/DOM/Using_fullscreen_mode)为一个网页或者应用程序控制使用整个屏幕，而不显示浏览器界面。

[指针锁定 API](https://developer.mozilla.org/zh-CN/docs/API/Pointer_Lock_API)允许锁定到内容的指针，这样游戏或者类似的应用程序在指针到达窗口限制时也不会失去焦点。

[在线和离线事件](https://developer.mozilla.org/zh-CN/docs/Online_and_offline_events)为了构建一个良好的具有离线功能的 web 应用程序，你需要知道什么时候你的应用程序确实离线了。顺便提一句，在你的应用程序又再回到在线状态时你也需要知道。  


