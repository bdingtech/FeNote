---
description: 花了六个多小时看了一下JavaScript高级程序设计中原型这一块的论述，感觉受益匪浅，现在在这里总结做一下笔记，便于日后复习
---

# 原型和原型链

## 什么是原型

在介绍原型之前，我们先要了解两个ECMA规范

#### 1.每个函数都会自动的创建一个 `Prototype` 属性

![prototype](../.gitbook/assets/image%20%2828%29.png)

#### 2.所有的 Object 都有一个默认的隐式引用

> Every object has an implicit reference \(called the object's prototype\)

![\_\_proto\_\_](../.gitbook/assets/image%20%2829%29.png)

好了现在我们知道有两种类型的原型了，一种是函数中的 `prototype` _显式原型_，另一种是对象中_隐式原型，_由这两种原型模型组成 JavaScript 强大的共享机制，在 JavaScript 语言中并不支持类与继承，但是通过原型特性，我们可以模拟继承。

## 指向什么







