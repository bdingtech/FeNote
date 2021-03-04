# 实现bind

首先我们来看一下 bind 有什么用

```javascript
  let person = {
      name:'pudding'
  }
  let name = 'this is window scope'
  function say(){
      console.log(this.name)
  }

  console.log(say.bind(person)) //[Function: bound say]
```

我们能看到 bind 有两个特点

1. 能够改变this指向和传入参数，作用和 call 类似
2. 返回的是函数

## 第一版：实现改变指向，和返回函数

```javascript
Function.prototype.myBind = function (obj){
    //因为这里是返回一个函数，所以需要保存当前调用的方法
    let self = this
    return function(){
        self.apply(obj)
    }
}
```

好了，现在我们通过apply实现了返回一个改变了this指向的一个函数

## 第二版：实现传入参数

#### ES6方法

```javascript
Function.prototype.myBind2 = function(obj,...args){
    let self = this
    return function(...args1){
        self.apply(obj,[...args,...args1])
    }
}
```

#### ES5方法

```javascript
Function.prototype.bind3 = function(obj){
    let self = this
    //获取参数
    let args = Array.prototype.slice.call(arguments,1)//等同于arguments.slice(1)
    return function(){
        let args1 = Array.prototype.slice.call(arguments,0)
        self.apply(obj,args.concat(args1))
    }
}
```

> 补充
>
> 这种方式形如this.max\(...numArray\)，都上面的arguments转换一样，都是利用了语法的特性
>
> ```javascript
> function getMaxOfArray(numArray) {    
>     return Math.max.apply(null, numArray);
> }
> ```

