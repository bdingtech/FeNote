---
description: >-
  TypeScript是JavaScript类型的超集，它可以编译成纯JavaScript。TypeScript可以在任何浏览器、任何计算机和任何操作系统上运行，并且是开源的。
---

# TypeScript

## 基本用法

### 定义基本的数据类型

原始数据类型： String、Number、Null、Undefind、BigInt、Symbols

引用数据类型：Object \( 包括：Array \)

```typescript
let isDone: boolean = false
let age: number = 10
let firstName:tring =  "1"

let u: undefined = undefied
let n: null = null

let num: number = undefinde

```

###  定义 Any 数据类型

 Any 的话就是说什么都可，和 JavaScript 差不多

```typescript
let notSure: Any = 4
notSure = 'maybe a string'
notSure = true
```

###  定义数组数据类型

> [数组](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/Array)是一种使用整数作为键\(integer-key-ed\)属性和长度\(length\)属性之间关联的常规**对象**。——MDN

```typescript
let arr:number[] = [1,2]
let str:string[] = ['1','2']
let mix:[string,number] = ['1',2]//需要一一对应
arr.push(3)//push 进去的值也需要满足定义
```

### 定义对象数据类型

> 使用 接口 （ interface ）来对对象的形状（ shape ）来进行描述，可以规定对象长什么样子，如果有不同的话则报错

```typescript
interface Person{
    name: string,
    age: number
}
let pudding: Person = {
    name: 'pudding',
    age: 1
}
```

###  定义函数的数据类型

```typescript
function add(x:number,y:number){
    return x+y
}
```

## 进阶用法

###  联合类型（ Union types ）和类型断言

> 在联合属性中只能访问所定义类型共有的方法，否则将会报错

```typescript
let numberOrstring: string | number
//报错 
//类型“string | number”上不存在属性“length”。类型“number”上不存在属性“length”。ts(2339)
numberOrstring.length()

numberOrstring.toString()
```

> 使用**类型断言**可以突破这种限制

```typescript
function  getLength(input:string | number): number{
    // const str = input.length //报错，应为 number中不存在.length方法
    const str = input as string
    if(str.length){
        return str.length
    }else{
        let number = input as number
        return number.toString().length
    }
}
```

