---
description: 在日常开发中，经常要与数组和对象打交道，这里就来总结一下遍历数组和对象的一些方法
---

# 数组的遍历以及对象的遍历

###  

![20 &#x79CD;&#x6570;&#x7EC4;&#x64CD;&#x4F5C;&#x65B9;&#x6CD5;](../.gitbook/assets/image%20%284%29.png)

### 前言

 说起来好笑😁，这个问题是这么被提出来的，本来是想研究**如何判断对象为空**这个问题的，后面去查资料，发现要通过 for..in 、枚举之类的，顿时我又看不懂了，这都啥玩意啊，平时也没用过 for...in 这玩意啊，但是出现率确实挺高的，遂找资料去了解了一下，害！终究还是太菜了！

###  数组的遍历

####  for 循环

 最原始的方法、也是最不优雅的方法之一。原因随随便便 for 循环，大一新生刚学 `C 语言`都会，没啥逼格

```javascript
var a = ["a", "b", "c"];
for(var index = 0;index < a.length;index++){
  console.log(a[index]);
}
```

####  forEach 遍历

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



