---
description: 腾讯csig二面的时候问到了Map和普通对象的区别，现在来总结一下
---

# Map、WeakMap

## Map

**`Map`** 对象保存键值对，并且能够记住键的原始插入顺序**。任何值\(对象或者**[**原始值**](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)**\) 都可以作为一个键**或一个值。

### 存取操作

```javascript
let myMap = new Map();

let keyObj = {};
let keyFunc = function() {};
let keyString = 'a string';

// 添加键
myMap.set(keyString, "和键'a string'关联的值");
myMap.set(keyObj, "和键keyObj关联的值");
myMap.set(keyFunc, "和键keyFunc关联的值");

myMap.size; // 3

// 读取值
myMap.get(keyString);    // "和键'a string'关联的值"
myMap.get(keyObj);       // "和键keyObj关联的值"
myMap.get(keyFunc);      // "和键keyFunc关联的值"

myMap.get('a string');   // "和键'a string'关联的值"
                         // 因为keyString === 'a string'
myMap.get({});           // undefined, 因为keyObj !== {}
myMap.get(function() {}); // undefined, 因为keyFunc !== function () {}
```

### 与 Object 对象的区别

[`Objects`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object) 和 `Maps` 类似的是，它们都允许你按键存取一个值、删除键、检测一个键是否绑定了值。因此（并且也没有其他内建的替代方式了）过去我们一直都把对象当成 `Maps` 使用。不过 `Maps` 和 `Objects` 有一些重要的区别

| 区别 | Map | Object |
| :--- | :--- | :--- |
| 键的类   型   | 一个 `Map`的键可以是**任意值**，包括函数、对象或任意基本类型。 | 一个`Object` 的键必须是一个 [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) 或是[`Symbol`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol)。 |
| 键的顺序 | `Map` 中的 key 是有序的。因此，当迭代的时候，一个 `Map` 对象以插入的顺序返回键值。 | 一个 `Object` 的键是无序的 |
| 其他键 | Map默认情况下仅包含显示插入的键 | Object有一个原型，可能会访问到原型上面的键 |
| Size |  `Map` 的键值对个数可以轻易地通过[`size`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map/size) 属性获取 | Object的键值对只能手动计算 |
| 性能 | 在频繁增删键值对的场景下表现更好。 | 在频繁添加和删除键值对的场景下未作出优化。 |

## WeakMap

**`WeakMap`** 对象是一组键/值对的集合，其中的键是弱引用的。**其键必须是对象**，而值可以是任意的。

### 什么是WeakMap？以及应该什么时候是用它？

在 JavaScript 里，map API 可以通过使其四个 API 方法共用两个数组\(一个存放键,一个存放值\)来实现。给这种 map 设置值时会同时将键和值添加到这两个数组的末尾。从而使得键和值的索引在两个数组中相对应。当从该 map 取值的时候，需要遍历所有的键，然后使用索引从存储值的数组中检索出相应的值。

但这样的实现会有两个很大的缺点，首先赋值和搜索操作都是 O\(n\) 的时间复杂度\( n 是键值对的个数\)，因为这两个操作都需要遍历全部整个数组来进行匹配。另外一个缺点是可能会导致内存泄漏，因为数组会一直引用着每个键和值。这种引用使得垃圾回收算法不能回收处理他们，即使没有其他任何引用存在了。

相比之下，原生的 WeakMap 持有的是每个键对象的“弱引用”，这意味着在没有其他引用存在时垃圾回收能正确进行。原生 WeakMap 的结构是特殊且有效的，其用于映射的 key 只有在其没有被回收时才是有效的。

正由于这样的弱引用，`WeakMap` 的 key 是不可枚举的 \(没有方法能给出所有的 key\)。如果key 是可枚举的话，其列表将会受垃圾回收机制的影响，从而得到不确定的结果。因此，如果你想要这种类型对象的 key 值的列表，你应该使用 [`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map)。

基本上，如果你要往对象上添加数据，又不想干扰垃圾回收机制，就可以使用 WeakMap。

