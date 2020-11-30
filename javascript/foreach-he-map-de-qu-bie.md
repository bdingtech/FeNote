---
description: 这个问题困扰了我很久，虽然以前去查过，但是现在似乎又忘了啥区别
---

# forEach 和 map 的区别

 在百度上查了好几篇文章，说法不一，经过查询 MDN 文档以及自己手工测试，以下内容基本上真实可靠

###  相同点

1. 都是循环便利数组的每一项
2. 每次执行匿名函数都支持三个参数，分别是 item（ 当前的数组项 ）、index（ 索引值 ）、arr（ 原数组 ）
3. 匿名函数的 this 都是指向 window
4. 只能便利数组
5. 都不修改调用它的原数组本身（**当然可以在 `callback` 执行时改变原数组**）
6. 除了抛出异常外，没有办法终止或者跳出循环

### 不同点

 map 会分配内存空间，存储新数组，然后返回

 forEach 不会返回数组

### 最佳实践

MDN 给出的最佳实践为

> 因为`map`生成一个新数组，当你不打算使用返回的新数组却使用`map`是违背设计初衷的，请用[`forEach`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)或者[`for-of`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...of)替代。你不该使用`map`: A\)你不打算使用返回的新数组，或/且 B\) 你没有从回调函数中返回值。 因为`map`生成一个新数组，当你不打算使用返回的新数组却使用`map`是违背设计初衷的，请用[`forEach`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)或者[`for-of`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...of)替代。你不该使用`map`: A\)你不打算使用返回的新数组，或/且 B\) 你没有从回调函数中返回值。

 推荐使用 forEach 的情况

1. 不打算返回新数组
2. 没有从回调函数中返回值

 需要提前终止或者跳出循环的情况不建议使用一下方法

* 一个简单的 [for](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for) 循环
* [for...of](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...of) / [for...in](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...in) 循环
* [`Array.prototype.every()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/every)
* [`Array.prototype.some()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/some)
* [`Array.prototype.find()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
* [`Array.prototype.findIndex()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

