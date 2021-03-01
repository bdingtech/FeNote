# 01上帝的钥匙 Object.defineProperty

## 什么是 Object.definProperty

**`Object.defineProperty()`** 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性，并返回此对象。——MDN

```javascript
let obj = {}
Object.defineProperty(obj,'username',{
    value:'pudding',
    enumerable:false,//是否可枚举
    configurable,//是否可以通过delete删除
})
console.log(obj.username) //pudding
```

正如MDN定义中所所说，Object.defineProperty 可以直接在一个对象上定义一个新的属性，这里需要注意的一个点事，需要实现定义一个对象，Object.definePrperty并不会创建一个对象

## 两大利器

`get`属性的 getter 函数，如果没有 getter，则为 `undefined`。当访问该属性时，会调用此函数。执行时不传入任何参数，但是会传入 `this` 对象（由于继承关系，这里的`this`并不一定是定义该属性的对象）。**该函数的返回值会被用作属性的值。**  
**默认为** [**`undefined`**](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)。

`set`属性的 setter 函数，如果没有 setter，则为 `undefined`。当属性值被修改时，会调用此函数。该方法接受一个参数（也就是被赋予的新值），会传入赋值时的 `this` 对象。  
**默认为** [**`undefined`**](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)。

这里所说的两大利器莫过于`setter`和`getter`了，在使用Object.defineProperty的同时，我们可以设置这两个属性，来对对象的读取和设置进行监控和拦截

```javascript
let obj = {}
Object.defineProperty(obj,'username',{
    get:function get(value) {
        console.log('你正在尝试读取值')
    }
})
console.log(obj.username) 
//你正在尝试读取值
//undefined

```

## 简单的响应式模型

有了上面的基础后，我们就可以根据这两个访问器属性来构建一个简单的响应式模型了

```javascript
function defineReactive(obj,key,value){
    Object.defineProperty(obj,key,{
        enumerable:true,
        configurable:true,
        get(){
            console.log('读取')
            return value
        },
        set(newValue){
            console.log('设置')
            if(newValue === value){
                return
            }
            value = newValue
        }
    })
}
let person = {}
defineReactive(person,'value',10)
console.log(person.value)
//读取
//10

```



