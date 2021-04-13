---
description: 面试官见我Map和普通对象的区别不会，转眼又问了Set和普通数组的区别，？？？，好吧，又不会，抓紧个时间补一下下
---

# Set、WeakSet

## Set

`Set` 类似于数组，但是成员的值都是唯一的，没有重复的值。

#### 创建

```javascript
var s = new Set();
s.add('haha');
s.size; // 1

typeof s;                          // "object"
s instanceof Object;               // true
Object.prototype.toString.call(s); // "[object Set]"
```

#### 属性

* `Set.prototype.constructor`：构造函数，默认就是Set函数。
* `Set.prototype.size`：返回Set实例的成员总数。

#### 方法

`Set` 的方法都是继承于原型，`Set.prototype.add(value)`。

操作方法：

* `add(value)`：添加某个值，返回 Set 结构本身。
* `delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
* `has(value)`：返回一个布尔值，表示该值是否为Set的成员。
* `clear()`：清除所有成员，没有返回值。

遍历方法：

* `keys()`：返回键名的遍历器
* `values()`：返回键值的遍历器
* `entries()`：返回键值对的遍历器（键名、键值相同）
* `forEach()`：使用回调函数遍历每个成员，但没有返回值

### 数组去重

```javascript
// Use to remove duplicate elements from the array
const numbers = [2,3,4,4,2,3,3,4,4,5,5,6,6,7,5,32,3,4,5]
console.log([...new Set(numbers)])
// [2, 3, 4, 5, 6, 7, 32]
```

## WeakSet

### 与Set的区别

WeakSet 结构与 Set 类似，也是不重复的值的集合。但是，它与 Set 有几个区别：

1. WeakSet 的成员只能是对象，而不能是其他类型的值
2. WeakSet 中的对象都是弱引用，如果其他对象都不再引用该对象，那么垃圾回收机制会自动回收该对象所占用的内存，不考虑该对象还存在于 WeakSet 之中
3. WeakSet 没有 size 属性，也无法使用 遍历操作

### 创建

```text
const a = [[1, 2], [3, 4]];
const ws = new WeakSet(a);
// WeakSet {[1, 2], [3, 4]}

Object.prototype.toString.call(ws) // "[object WeakMap]"
复制代码
```

#### 可用方法

`add()`、`delete()`、`has()`

### 使用场景

**1. 避免内存泄露**

由于 WeakSet 不再使用的时候，会被自动回收，所以可以用来存储 DOM 节点，而不用担心这些节点从文档移除时会引发内存泄露。

```javascript
const foos = new WeakSet()
class Foo {
  constructor() {
    foos.add(this)
  }
  method () {
    if (!foos.has(this)) {
      throw new TypeError('Foo.prototype.method 只能在Foo的实例上调用！');
    }
  }
}
```

上面代码保证了Foo的实例方法，只能在Foo的实例上调用。这里使用 WeakSet 的好处是，foos对实例的引用，不会被计入内存回收机制，所以删除实例的时候，不用考虑foos，也不会出现内存泄漏。  


