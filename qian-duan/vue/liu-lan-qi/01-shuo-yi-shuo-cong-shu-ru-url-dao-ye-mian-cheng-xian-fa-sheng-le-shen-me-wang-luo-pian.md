---
description: 作为第一步，我们看看浏览器是如何把页面通过网络给请求回来的
---

# 01说一说从输入URL到页面呈现发生了什么-网络篇

这个标题是借鉴了三元博客上的总结，他把这个过程分为**网络篇**、**解析篇**、**渲染篇**，可以看出还是别有用心的。浏览器就像一个黑箱，把一堆文件给丢进去，他就自动生成页面了，但是他是如何生成的，估计很多人就回答不上来了。

> 这是一个可以无限难的问题。这里我提前声明，由于是一个综合性非常强的问题，可能会在某一个点上深挖出非常多的细节，我个人觉得学习是一个循序渐进的过程，在明白了整体过程后再去自己研究这些细节，会对整个知识体系有更深的理解。同时，关于延申出来的细节点我都有参考资料，看完这篇之后不妨再去深入学习一下，扩展知识面。——引用自三元博客

## 1.准备发起请求

当浏览器做完一些准备工作（容错处理、修改导航栏状态等）后，就会将 URL 通过进程间通讯（ IPC ）发过给网络进程，在网络进程里发起真正的请求

## 2.查找缓存

检查本地是否存在强缓存，如果有则直接返回缓存的文件，没有的话再根据缓存策略判断是直接请求还是走协商缓存

## 3.DNS查询

由于网络进程得到的是URL，而数据包是通过IP传给对方的，所以这时候我们需要得到URL所对应的IP地址，这时候就要用到DNS查询，由于DNS要求速度快，所以采用的是UDP协议，通过DNS查询，我们现在得到了IP地址，可以发起 HTTP 请求了。

除此之外，浏览器也会对已经解析过了域名进行缓存，当命中的时候就直接返回，而不再发起DNS查询了

![DNS&#x67E5;&#x8BE2;&#x8FC7;&#x7A0B;](../../../.gitbook/assets/image%20%2865%29.png)

## 4.建立TCP连接

在发起HTTP请求时，我们得先建立TCP连接，而建立TCP连接经历了一下几个过程

1. **三次握手建立连接**，客户端首先发一个包给服务器（发），服务器接收到后响应一个请求（收发），客户端再发送一个包\(收\)，通过三个数据包，**确定了客户端和服务器双方都具有收发能力**
2. **传输数据**
3. 四次挥手断开连接

更多TCP细节详细内容参见

{% page-ref page="../../shu-zu-he-dui-xiang/wang-luo/tcp.md" %}

## 5.发起HTTP请求

有了下层传输层TCP给我们建立好的通道，现在我们就可以愉快的和服务端交流啦，浏览器发送一个HTTP请求需要包含三样东西，请求头、请求行、请求体

![&#x53D1;&#x8D77;http&#x8BF7;&#x6C42;](../../../.gitbook/assets/image%20%2870%29.png)

## 6.响应网络请求

客户端发送的HTTP请求到达服务端后，服务端会进行相应的处理，最后返回网页文件，也就是响应网络请求

![&#x54CD;&#x5E94;&#x62A5;&#x6587;&#x7684;&#x6784;&#x6210;](../../../.gitbook/assets/image%20%2869%29.png)

响应完成之后怎么办？TCP 连接就断开了吗？

不一定。这时候要判断`Connection`字段, 如果请求头或响应头中包含**Connection: Keep-Alive**，表示建立了持久连接，这样`TCP`连接会一直保持，之后请求统一站点的资源会复用这个连接。

否则断开`TCP`连接, 请求-响应流程结束。

至此我们得到了网站返回的文件，接下来就是最神秘的地方——浏览器如何根据返回HTML、CSS、JavaScript文件构建出精妙的网页

## 总结

![](../../../.gitbook/assets/image%20%2871%29.png)

## 附录

网络包的旅途——《网络是怎么连接的》

![](../../../.gitbook/assets/image%20%2863%29.png)

![](../../../.gitbook/assets/image%20%2875%29.png)
