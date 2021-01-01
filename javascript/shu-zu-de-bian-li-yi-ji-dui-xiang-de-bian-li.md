---
description: 在日常开发中，经常要与数组和对象打交道，这里就来总结一下遍历数组和对象的一些方法
---

# 常用数组遍历和对象遍历方法【待补充】

###  

![20 &#x79CD;&#x6570;&#x7EC4;&#x64CD;&#x4F5C;&#x65B9;&#x6CD5;](../.gitbook/assets/image%20%284%29.png)

## 前言

 说起来好笑😁，这个问题是这么被提出来的，本来是想研究**如何判断对象为空**这个问题的，后面去查资料，发现要通过 for..in 、枚举之类的，顿时我又看不懂了，这都啥玩意啊，平时也没用过 for...in 这玩意啊，但是出现率确实挺高的，遂找资料去了解了一下，害！终究还是太菜了！

##  数组的遍历

###  for 循环

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

##  对象的遍历



