---
description: 最后一步了
---

# 03说一说输入URL到页面呈现发生了什么-渲染篇

首先我们先来回顾一下，在渲染前发生了什么，首先是构建DOM树，也就是解析HTML，然后再是样式计算，计算出每个DOM节点的样式，也就是CSS解析，然后就是生成布局树

但是，并不是说生成布局树后就完事了，就可以渲染了，那就太天真了

因为你考虑掉了另外一些复杂的场景，比如3D动画如何呈现出变换效果，当元素含有层叠上下文时如何控制显示和隐藏等等。

为了解决如上所述的问题，浏览器在构建完`布局树`之后，还会对特定的节点进行分层，构建一棵`图层树`\(`Layer Tree`\)。

## 1.构建图层树

其实我们在浏览器上面看到的页面，都是由一层一层叠起来之后的效果，所以，第一步就是创建图层树，具体我就不深究了，感兴趣的可以去看看《浏览器工作原理与实践》

![](../../.gitbook/assets/image%20%2874%29.png)

## 2.生成绘制列表

接下来渲染引擎会将图层的绘制拆分成一个个绘制指令，比如先画背景、再描绘边框......然后将这些指令按顺序组合成一个待绘制列表，相当于给后面的绘制操作做了一波计划。

## 3.生成图块和生成位图（栅格化操作）

现在开始绘制操作，实际上在渲染进程中绘制操作是由专门的线程来完成的，这个线程叫**合成线程**。

绘制列表准备好了之后，渲染进程的主线程会给`合成线程`发送`commit`消息，把绘制列表提交给合成线程。接下来就是合成线程一展宏图的时候啦。

![](../../.gitbook/assets/image%20%2873%29.png)

通常一个页面可能很大，但是用户只能看到其中的一部分，我们把用户可以看到的这个部分叫做视口（viewport）。在有些情况下，有的图层可以很大，比如有的页面你使用滚动条要滚动好久才能滚动到底部，但是通过视口，用户只能看到页面的很小一部分，所以在这种情况下，要绘制出所有图层内容的话，就会产生太大的开销，而且也没有必要。

合成线程要做的第一件事情就是将图层**分块**。这些块的大小一般不会特别大，通常是 256 \* 256 或者 512 \* 512 这个规格。这样可以大大加速页面的首屏展示。

然后合成线程会选择视口附近的**图块**，把它交给**栅格化线程池**生成位图。所谓栅格化，是指将图块转换为位图。

## 4.显示器显示内容

栅格化操作完成后，**合成线程**会生成一个绘制命令，即"DrawQuad"，并发送给浏览器进程。

浏览器进程中的`viz组件`接收到这个命令，根据这个命令，把页面内容绘制到内存，也就是生成了页面，然后把这部分内存发送给显卡。为什么发给显卡呢？我想有必要先聊一聊显示器显示图像的原理。

无论是 PC 显示器还是手机屏幕，都有一个固定的刷新频率，一般是 60 HZ，即 60 帧，也就是一秒更新 60 张图片，一张图片停留的时间约为 16.7 ms。而每次更新的图片都来自显卡的**前缓冲区**。而显卡接收到浏览器进程传来的页面后，会合成相应的图像，并将图像保存到**后缓冲区**，然后系统自动将`前缓冲区`和`后缓冲区`对换位置，如此循环更新。

看到这里你也就是明白，当某个动画大量占用内存的时候，浏览器生成图像的时候会变慢，图像传送给显卡就会不及时，而显示器还是以不变的频率刷新，因此会出现卡顿，也就是明显的掉帧现象。

到这里，经过这一系列的阶段，编写好的 HTML、CSS、JavaScript 等文件，经过浏览器就会显示出漂亮的页面了。





