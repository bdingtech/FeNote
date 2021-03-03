---
description: >-
  instanceof 的发明是为了弥补 typeof 所带来的缺陷，因为 typeof 在检测 object 类型的时候，总是会返回object，所以 js
  提供了另外一个接口来实现对对象类型的判断，那就是我们的 instanceof
---

# 实现 instanceof

`instanceof`是基于原型链判断的

```javascript
/**
 * 实现自己的instanceof
 * 原理：判断变量的隐式引用（__proto__）是否在原型链上
 */
 function myInstanceof(left, right){
    //先获取原型对象
    let leftProto = left.__proto__
    let rightProto = right.prototype
    //不断遍历
    while(true){
        if(leftProto === rightProto){
            return true
        }
        //当指针到原型链的顶部时，也就是指向null的时候就停止遍历
        if(leftProto === null){
            return false
        }
        //不断将指针往后指
        leftProto = leftProto.__proto__
    }
 }
 let res = myInstanceof(arr,Number)
 console.log(res)//false
 
  let res = myInstanceof(arr,Array)
 console.log(res)//true
 
   let res = myInstanceof(arr,Object)
 console.log(res)//true
```

