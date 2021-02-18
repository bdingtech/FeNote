---
description: >-
  作为前端三剑客之中最重要的一环，JavaScript经历了被人唾弃到万众瞩目的华丽蜕变。人生如逆旅，我亦是行人，要向JavaScript学习，默默无闻的改变着自己！
---

# JavaScript 篇

## 原型对象和原型链

JavaScript中引入了原型与原型链的概念，通过这种共享关系，使得所有对象都能共享原型的方法，**节省内存，**而又通过继承关系，通过制定不同的原型，又能很好的模**拟「类」的行为**。

### 什么是原型对象，什么是原型链，说一说你的理解？

## 作用域和闭包

> 闭包就好像从 JavaScript 中分离出来的一个充满神秘色彩的未开化世界，只有最勇敢的人 才能够到达那里。——《你不知道的JavaScript 上卷》

### 说一说JavaScript中的作用域



### 闭包是什么？

闭包是一种能够在函数声明过程中将**环境信息（父函数的作用域）**与**所属函数**绑定在一起的**数据结构**

```javascript
function makeAddFunction(amount){
    function add(number){
        return number + amount
    }
    return add
}
```

```javascript
//利用闭包实现一个计数器
let test = (function count(){
    let num = 0
    function addNum(){
        num++
        console.log(num)
    }
    return addNum
})()
test() //1
test() //2
test() //3
```

