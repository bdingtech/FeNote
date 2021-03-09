---
description: 作为一个前端开发工程师，跨域问题是必定会遇到的一个坎，这时候我们也要努把力跳过去，不能畏畏缩缩的
---

# 什么是跨域，怎么解决？

刚开始进行前后端交互的时候，可能会比较困惑，明明自己代码里面向服务端发送了请求，在浏览器Network里面也看到了，但是console.log打印的时候确是undefind，这就有点诡异，然后再看浏览器也会有一条报错，

![](../../.gitbook/assets/image%20%2897%29.png)

然后这时候你复制关键字，去百度或者谷歌上查，最后得到的答案是遇到了跨域问题

## 什么跨域

简单来说就是向目标 URL 发送请求的时候，只要**协议**、**域名**、**端口**，这三者有一个不相同就属于跨域

浏览器遵循**同源政策**\(`scheme(协议)`、`host(主机)`和`port(端口)`都相同则为`同源`\)。非同源站点有这样一些限制:

* 不能读取和修改对方的 DOM
* 不读访问对方的 Cookie、IndexDB 和 LocalStorage
* 限制 XMLHttpRequest 请求。\(后面的话题着重围绕这个\)

### 为什么浏览器会拦截跨域请求？

**为了安全**。仔细想一想，假如浏览器放通一切请求，那么当你打开这个网页的时候，我就可以向你的支付宝、知乎、甚至是你的银行账户（假设他们都没有做任何防护\)发动请求，这时候我就能得到你的支付宝余额，支付宝私信等等，甚至还可以悄悄转走你银行账户里面的余额（csrf），现在是不是觉得拦截跨域访问至关重要了

## 如何跨域

浏览器强大的跨域机制，导致我们日常开发过程中人畜无害的请求也被拦截了，这时候我们十分清楚，这些请求是我们自己人为可控的，所以就必须采取一些措施来规避这些限制

### Jsonp

首先，先概括一下他目前的jsonp应用状态。属于上一代的跨域方式，或者说是比较古老的方式，但是因为兼容性好，所以目前主要应用在一些需要兼容ie的场景下，缺点就是，只支持get请求

ajax会被浏览器的同源策略ban掉，但是我们的script标签并不会呀，所以我们使用一点技巧，构造一下，就能利用这个特性愉快的玩耍了，jsonp简单来说就是，我们构造一个回调函数，然后服务端将响应封装在回调函数中返回，我们本地就拿到了返回值了。上代码

#### 本地

```markup
<body>
  <script>
    function handleResponse(res) {
      console.log(res) // {text: "jsonp"}
    }

    const script = document.createElement('script')
    script.src = 'http://127.0.0.1:3000?callback=handleResponse'
    document.head.appendChild(script)
  </script>
</body>
```

#### 服务端

```javascript
const server = http.createServer((req, res) => {
  if (~req.url.indexOf('?callback')) { // 简单处理 JSONP 跨域的时候
    const obj = {
      "text": 'jsonp',
      "test":'puddingtest'
    }
    const callback = req.url.split('callback=')[1]
    const json = JSON.stringify(obj)
    const build = callback + `(${json})`
    res.end(build) // 这里最终返回前端的是相当于调用函数 callback({json})
  } else { // 非跨域的时候
    res.statusCode = 200
    res.setHeader('Content-Type', 'text/plain')
    res.end('Hello World\n')
  }
});

```

