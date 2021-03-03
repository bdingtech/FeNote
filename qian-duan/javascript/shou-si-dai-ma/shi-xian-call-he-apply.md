# 实现 call 和 apply

## 实现 call 方法

### 第一版

能实现改变 this 指向了

```javascript
 /**
 * 原理
 * 将方法挂载在传进来的对象属性上
 * 然后再执行
 * 最后再删除掉该属性
 */
 function myCall(obj){
     let key = Symbol()
     //将调用方法挂载到独享属性上
    obj[key] = this
    //执行
    obj[key]()
    //删除
    delete obj[key]
 }
```

### 第二版

能实现传入参数了

#### 使用展开运算符

```javascript
function myCall1(obj){
     let key = Symbol()
     obj[key] = this
     //获取参数
     let args = []
     //从arguments的第2位开始
     for(let i = 1; i < arguments.length; i++){
         args.push(arguments[i])
     }
     //然后再执行的时候将数组传进去
     obj[key](...args)
     delete obj[key]
 }
```

#### 使用eval

call 是 ES3 的语法，使用 ES6 的展开运算符，好像有点不讲武德，所以这里我们使用eval来进行值传递

```javascript
 function myCall2 (obj){
     obj.fn = this
     var args = []
     for(var i = 1; i < arguments.length; i++){
         args.push('arguments[' + i + ']')
     }
     eval('obj.fn(' + args + ')')
     delete obj.fn
 }
```

### 第三版-最终完整版

兼容null，如果没有对call进行传值或者传的是null的话，this是指向window的，最后还要return结果

#### ES6版本

```javascript
function myCall3(obj = window, ...args) {
  if (typeof this != "function") {
    throw new TypeError("Not Function");
  }
  let key = Symbol();
  obj[key] = this;
  let result = obj[key](args);
  delete obj[key];
  return result
}
```

#### ES3版本

```javascript
function myCall4(obj){
    if(typeof this != 'function'){
        throw new TypeError('Not Function')
    }
    obj = obj || window
    obj.fn = this
    var args = []
    for(var i = 1; i < arguments.length; i++){
        args.push('arguments(' + i + ')')
    }
    var result = eval('obj.fn(' + args + ')')
    delete obj.fn
    return result
}
```



