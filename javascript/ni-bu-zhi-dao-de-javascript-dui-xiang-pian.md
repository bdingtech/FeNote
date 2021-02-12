# 你不知道的JavaScript——对象篇

## JavaScript中有一些什么数据类型

包括`bigInt`的话总共有 **7** 种数据类型：

`String`、`Number`、`Boolean`、`Null`、`Undefined`、`Symbols`、`BigInt`

## typeof null 返回什么？为什么？

typeof 返回的是 'Object' ，但是 null 却是一个基本类型，这其实是 JavaScript 本身的一个 bug ，应为在底层是通过二进制来表示不同的对象，前三位代表数据类型，如果全为 0 的话会被判定为 Object 类型，而null 的二进制全都是 0 ，前三位自然也是了，所以执行 typeof 的时候会返回 ‘Object’

