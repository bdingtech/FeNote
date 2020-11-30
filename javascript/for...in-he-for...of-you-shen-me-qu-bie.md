---
description: 虽然作为前端菜鸡的我在平时写项目中的时候还没用到这两玩意，但是想着未雨绸缪为以后做准备，所以我就来理一下这两玩意了
---

# for...in 和 for...of 有什么区别？

##  定义

 我们先来看看 MDN 是怎么定义这两个玩意的

###  for...in

![MDN &#x4E0A;&#x5BF9; for...in &#x7684;&#x5B9A;&#x4E49;](../.gitbook/assets/image%20%287%29.png)

###  for...of

**`for...of`语句**在[可迭代对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/iterable)（包括 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array)，[`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Map)，[`Set`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set)，[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String)，[`TypedArray`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypedArray)，[arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments) 对象等等）上创建一个迭代循环，调用自定义迭代钩子，并为每个不同属性的值执行语句

![MDN &#x4E0A;&#x5BF9; for..of &#x7684;&#x5B9A;&#x4E49;](../.gitbook/assets/image%20%2811%29.png)

##  区别

###  服务对象不同

 可以从上图看出来，两者语法结构一模一样，从定义上来看还有些区别的，for...in 的所设计处理的是**对象**，而 for... of 则是[**可迭代对象**](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Iteration_protocols)

**可迭代协议**允许 JavaScript 对象定义或定制它们的迭代行为，例如，在一个 [`for..of`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...of) 结构中，哪些值可以被遍历到。一些内置类型同时是[内置可迭代对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Iteration_protocols#%E5%86%85%E7%BD%AE%E5%8F%AF%E8%BF%AD%E4%BB%A3%E5%AF%B9%E8%B1%A1)，并且有默认的迭代行为，比如 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array) 或者 [`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Map)，而其他内置类型则不是（比如 [`Object`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object)\)）。

 可以看到 Object 并不是内置迭代协议，所有 for...of 并不支持迭代普通对象

###  variable 值不同

 可以看到 for...in 所得到的值为字符串型，不能作为几何运算

![](../.gitbook/assets/image%20%288%29.png)

###  for...in 会遍历数组所有的可枚举属性，包括原型

![](../.gitbook/assets/image%20%285%29.png)

## 总结

* for..of 适用遍历数/数组对象/字符串/ map / set 等拥有迭代器对象的集合.但是不能遍历对象,因为没有迭代器对象.与forEach\(\)不同的是，它可以正确响应break、continue和return语句
* for-of循环不支持普通对象，但如果你想迭代一个对象的属性，你可以用for-in循环（ 这也是它的本职工作 ）或内建的 Object.keys\(\) 方法
* **遍历对象用 for..in、遍历数组用 for...of**

