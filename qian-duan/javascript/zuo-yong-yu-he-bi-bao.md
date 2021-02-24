---
description: 闭包就好像从 JavaScript 中分离出来的一个充满神秘色彩的未开化世界，只有最勇敢的人 才能够到达那里。——《你不知道的JavaScript 上卷》
---

# 作用域和闭包

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

### 在日常开发中，闭包有一些什么实际用途？

> 我就不班门弄斧了，这里引用 《JavaScript函数式编程指南》中的总结

1. **模拟私有变量**，可以通过闭包这种数据结构将一些变量和方法隐藏起来，外界不能访问
2. **提供模块化开发机制**
3. **创建块级作用域**

