---
description: >-
  最早接触这玩意是在《浏览器工作原理与实践》中，当时看了之后也是迷迷糊糊，然后2.15下午觉得解决这个问题，就又跑去看了一遍，结果发现还是看不懂，后面在b站上找了一个视频看，发现好像也就那么回事
---

# 事件循环练习题

## 1.来自三元博客——[如何理解EventLoop浏览器篇](http://47.98.159.95/my_blog/blogs/javascript/js-v8/005.html)

```javascript
console.log('start');
setTimeout(() => {
  console.log('timeout');
});
Promise.resolve().then(() => {
  console.log('resolve');
});
console.log('end');
```

我们来分析一下:

1. 刚开始整个脚本作为一个宏任务来执行，对于同步代码直接压入执行栈\(关于执行栈，若不了解请移步之前的文章《JavaScript内存机制之问——数据是如何存储的？》\)进行执行，因此**先打印start和end**
2. setTimeout 作为一个宏任务放入宏任务队列
3. Promise.then作为一个为微任务放入到微任务队列
4. 当本次宏任务执行完，检查微任务队列，发现一个Promise.then, **执行**
5. 接下来进入到下一个宏任务——setTimeout, **执行**

因此最后的顺序是:

```text
start
end
resolve
timeout
```

## 2.来自[游览器工作原理与实践](https://time.geekbang.org/column/article/135624)

```javascript
function executor(resolve, reject) {
    let rand = Math.random();
    console.log(1)
    console.log(rand)
    if (rand > 0.5)
        resolve()
    else
        reject()
}
var p0 = new Promise(executor);

var p1 = p0.then((value) => {
    console.log("succeed-1")
    return new Promise(executor)
})


var p3 = p1.then((value) => {
    console.log("succeed-2")
    return new Promise(executor)
})

var p4 = p3.then((value) => {
    console.log("succeed-3")
    return new Promise(executor)
})


p4.catch((error) => {
    console.log("error")
})
console.log(2)
```



## 推荐资源

1. [Promise微任务处理逻辑](https://www.bilibili.com/video/BV1eJ41177Rg?p=3)



