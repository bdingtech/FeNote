---
description: 常见面试题
---

# Let、Const

## let

### 1.没有变量提升

```javascript
console.log(a); // 报错ReferenceError
let a = 2;
```

### 2.不允许重复声明变量

let不允许在相同作用域内，重复声明同一个变量

```javascript
function func(arg) {
  let arg; // 报错
}
```

### 3.let全局变量不会挂在顶层对象下面

var声明的全局变量会挂在顶层对象下面，而let不会挂在顶层对象下面

```javascript
var a = 1;
// 如果在 Node环境，可以写成 global.a
// 或者采用通用方法，写成 this.a
window.a // 1

let b = 1;
window.b // undefined
```

### 3.块级作用域

es6之前JavaScript中只有全局作用域和函数作用域，let声明变量可以实现块级作用域，“{}”之间就是一个块作用域

```javascript
function test() {
    for(var i = 0; i <= 10; i++) {
        
    }
    console.log(i)  //11, i是当前函数作用域下面的
}


function test1() {
    for(let i = 0; i <= 10; i++) {
        
    }
    console.log(i)  //报错ReferenceError
}


```

## const

* const 基本和 let 一样的特性，不过 const 声明的变量不能被修改（也就是一个常量）针对值，如果是对象或者数组内的属性是可以修改，基本数据类型和引用数据类型（地址值）的值不能被修改
* 一旦声明，必须马上赋值

```javascript
let p; var p1; // 不报错
const p3 = '马上赋值'
const p3; // 报错 没有赋值
```

