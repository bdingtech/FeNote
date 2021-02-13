---
description: HTTP是前端开发中接触到最多的应用层协议，搞清楚HTTP对开发会有比较大的帮助
---

# 网络篇-HTTP

## 什么时候会触发强制缓存或者协商缓存？

### 强制缓存

强缓存离不开两个响应头 Expires（ http1.0 ） 与 Cache-Control \( 较常用 \)

![](../.gitbook/assets/image%20%2848%29.png)

目前主流的做法使用 Cache-Control 控制缓存，除了 max-age 控制过期时间外，还有一些不得不提

* Cache-Control: public可以被所有用户缓存，包括终端和CDN等中间代理服务器
* Cache-Control: private只能被终端浏览器缓存，不允许中继缓存服务器进行缓存
* Cache-Control: no-cache,先缓存本地，但是在命中缓存之后必须与服务器验证缓存的新鲜度才能使用
* Cache-Control: no-store，不会产生任何缓存 

所以，当Cache-Control 设置为public或者private时，会触发强制缓存策略，为no-cache时，先缓存，但是只有和服务器验证之后才能时候

### 协商缓存

当请求头中没有Cache-Control和Expires时，或者过期的时候，则命中协商缓存

## HTTP的缓存的过程是怎样的?

1. 客户端向服务器发送请求
2. 服务器返回资源，并且通过响应头决定缓存策略
3. 客户端根据缓存策决定是否将资源缓存下来，分为两种情况，一种是强制缓存、一种是协商缓存
4. 当客户端再次发起请求时，则根据缓存策略，如果是强制缓存，则命中缓存后直接返回缓存资源，不再发起请求，如果是协商缓存，则将上一次浏览器返回的ETag或者Last-Modified发送给浏览器，由浏览器进行判断，如果是304则无需再次下载该资源，直接从缓存中读取，反之返回200，携带新的请求头和数据

### 第一次请求（无缓存）

![](../.gitbook/assets/image%20%2847%29.png)

HTTP缓存有多种规则，根据是否需要重新向服务器发起请求来分类，我将其分为两大类\(**强制缓存**，**协商缓存\)**

### **第二次请求-强制缓存**

缓存命中则直接返回，而未命中则向服务器返回数据

![](../.gitbook/assets/image%20%2846%29.png)

### 第二次请求-协商缓存

当第一次请求时服务器返回的响应头中没有Cache-Control和Expires或者Cache-Control和Expires过期抑或它的属性设 置为no-cache时，那么浏览器第二次请求时就会与服务器进行协商。

![](../.gitbook/assets/image%20%2849%29.png)

#### **Etag / If-None-Match**（优先级高于Last-Modified / If-Modified-Since）

#### **Last-Modified / If-Modified-Since**

