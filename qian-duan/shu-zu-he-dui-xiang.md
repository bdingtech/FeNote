# 数组和对象

## 数组的遍历

### for 循环

最原始的方法、也是最不优雅的方法之一。原因随随便便 for 循环，大一新生刚学 `C 语言`都会，没啥逼格

```javascript
var a = ["a", "b", "c"];
for(var index = 0;index < a.length;index++){
  console.log(a[index]);
}
```

优化版

```javascript
// 使用临时变量，将长度缓存起来，避免重复获取数组长度，当数组较大时优化效果才会比较明显。
for(let i = 0, len=arr.length; i < len; i++) {
   //代码
}

```

###  forEach 遍历

> **`forEach()`** 方法对数组的每个元素执行一次给定的函数。—— MDN

 自从ES5发布以后,可以用内建的`forEach`来遍历数组

```javascript
let arr = ['a','b','c']
arr.forEach((item) => {
    console.log(item)
})
```

{% hint style="warning" %}
缺点：不能用Break 退出循环，也不能 return 到上一层
{% endhint %}

###  map 遍历

```javascript
let arr = [1,2,3,4,5]
arr.map(item => {
    console.log(item)
})
```

{% hint style="info" %}
当不需要返回新数组时，使用 forEach 才是最佳实践
{% endhint %}

### for...of（ ES6 ）

MDN 给出的定义为

> **`for...of`语句**在[可迭代对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/iterable)（包括 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array)，[`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Map)，[`Set`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set)，[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String)，[`TypedArray`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypedArray)，[arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments) 对象等等）上创建一个迭代循环，调用自定义迭代钩子，并为每个不同属性的值执行语句

####  语法

```javascript
for (variable of iterable) {
    statement
}
//variable：每个迭代的属性值被分配给该变量。
//iterable：一个具有可枚举属性并且可以迭代的对象。实例
```

####  实例

```javascript
let arr = [1,2,3,4]
for(item of arr){
    console.log(item)
}
```

{% hint style="success" %}
优点是在优雅的同时可以支持跳出循环
{% endhint %}

## forEach 和 map 的区别

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

## for...in 和 for...of 有什么区别？

> 虽然作为前端菜鸡的我在平时写项目中的时候还没用到这两玩意，但是想着未雨绸缪为以后做准备，所以我就来理一下这两玩意了

### 定义

 我们先来看看 MDN 是怎么定义这两个玩意的

####  for...in

![MDN &#x4E0A;&#x5BF9; for...in &#x7684;&#x5B9A;&#x4E49;](../.gitbook/assets/image%20%288%29.png)

####  for...of

**`for...of`语句**在[可迭代对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/iterable)（包括 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array)，[`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Map)，[`Set`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set)，[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/String)，[`TypedArray`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypedArray)，[arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments) 对象等等）上创建一个迭代循环，调用自定义迭代钩子，并为每个不同属性的值执行语句

![MDN &#x4E0A;&#x5BF9; for..of &#x7684;&#x5B9A;&#x4E49;](../.gitbook/assets/image%20%2812%29.png)

###  区别

####  服务对象不同

 可以从上图看出来，两者语法结构一模一样，从定义上来看还有些区别的，for...in 的所设计处理的是**对象**，而 for... of 则是[**可迭代对象**](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Iteration_protocols)

**可迭代协议**允许 JavaScript 对象定义或定制它们的迭代行为，例如，在一个 [`for..of`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...of) 结构中，哪些值可以被遍历到。一些内置类型同时是[内置可迭代对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Iteration_protocols#%E5%86%85%E7%BD%AE%E5%8F%AF%E8%BF%AD%E4%BB%A3%E5%AF%B9%E8%B1%A1)，并且有默认的迭代行为，比如 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Array) 或者 [`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Map)，而其他内置类型则不是（比如 [`Object`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object)\)）。

 可以看到 Object 并不是内置迭代协议，所有 for...of 并不支持迭代普通对象

####  variable 值不同

 可以看到 for...in 所得到的值为字符串型，不能作为几何运算

![](../.gitbook/assets/image%20%289%29.png)

###  for...in 会遍历数组所有的可枚举属性，包括原型

![](../.gitbook/assets/image%20%285%29.png)

### 总结

* for..of 适用遍历数/数组对象/字符串/ map / set 等拥有迭代器对象的集合.但是不能遍历对象,因为没有迭代器对象.与forEach\(\)不同的是，它可以正确响应break、continue和return语句
* for-of循环不支持普通对象，但如果你想迭代一个对象的属性，你可以用for-in循环（ 这也是它的本职工作 ）或内建的 Object.keys\(\) 方法
* **遍历对象用 for..in、遍历数组用 for...of**

