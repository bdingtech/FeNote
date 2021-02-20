# 变量类型和类型转换

## 面试官：说一说`javascript`中有哪些数据类型?

最新的 `ECMAScript` 标准定义了 8 种数据类型:，包括**基本类型**和**引用类型**。（ [以MDN为准](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures) ）

<table>
  <thead>
    <tr>
      <th style="text-align:center">&#x9879;&#x76EE;</th>
      <th style="text-align:center">&#x57FA;&#x672C;&#x7C7B;&#x578B;</th>
      <th style="text-align:center">&#x5F15;&#x7528;&#x7C7B;&#x578B;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:center">&#x503C;</td>
      <td style="text-align:center">Number&#x3001;String&#x3001;Null&#x3001;Undefind&#x3001;BigInt&#x3001;Symbols&#x3001;Boolean</td>
      <td
      style="text-align:center">Object</td>
    </tr>
    <tr>
      <td style="text-align:center">&#x5B58;&#x50A8;&#x65B9;&#x5F0F;</td>
      <td style="text-align:center">&#x6808;&#x5185;&#x5B58;</td>
      <td style="text-align:center">&#x5806;&#x5185;&#x5B58;</td>
    </tr>
    <tr>
      <td style="text-align:center">&#x5B58;&#x50A8;&#x503C;</td>
      <td style="text-align:center">
        <p>&#x65B0;&#x7684;&#x53D8;&#x91CF;</p>
        <p>&#x53D8;&#x91CF;&#x6709;&#x81EA;&#x5DF1;&#x7684;&#x503C;</p>
      </td>
      <td style="text-align:center">
        <p>&#x6307;&#x9488;</p>
        <p>&#x6307;&#x5411;&#x5806;&#x5185;&#x5B58;&#x4E2D;&#x8BE5;&#x5BF9;&#x8C61;&#x7684;&#x5B58;&#x50A8;&#x5730;&#x5740;</p>
      </td>
    </tr>
  </tbody>
</table>

![   &#x57FA;&#x672C;&#x7C7B;&#x578B;&#x7684;&#x5B58;&#x50A8;&#x65B9;&#x5F0F;](../.gitbook/assets/image%20%282%29.png)

![&#x5F15;&#x7528;&#x7C7B;&#x578B;&#x7684;&#x5B58;&#x50A8;&#x65B9;&#x5F0F;](../.gitbook/assets/image%20%283%29.png)



**基本类型**分为以下八种：

* 布尔值（**Boolean**），有2个值分别是：`true` 和 `false`.
* **null** ， 一个表明 null 值的特殊关键字。 JavaScript 是大小写敏感的，因此 `null` 与 `Null`、`NULL`或变体完全不同。
* **undefined** ，和 null 一样是一个特殊的关键字，undefined 表示变量未定义时的属性。
* 数字（**Number**），整数或浮点数，例如： `42` 或者 `3.14159`。
* 任意精度的整数 \(**BigInt**\) ，可以安全地存储和操作大整数，甚至可以超过数字的安全整数限制。
* 字符串（**String**），字符串是一串表示文本值的字符序列，例如："Howdy" 。
* 代表（**Symbol**） \( 在 ECMAScript 6 中新添加的类型\).。一种实例是唯一且不可改变的数据类型。

`引用类型`为一种

* 对象（**Object**）

**注意**：

1. `string` 、`number` 、`boolean` 和 `null`、 `undefined` 这五种类型统称为**原始类型**（Primitive），表示不能再细分下去的基本类型;
2. `symbol`和`BigInt`是ES6中新增的数据类型，`symbol` 表示独一无二的值，通过 `Symbol` 函数调用生成，由于生成的 symbol 值为原始类型，所以 `Symbol` 函数不能使用`new` 调用；`BigInt`数据类型的目的是比`Number`数据类型支持的范围更大的整数值。在对大整数执行数学运算时，以任意精度表示整数的能力尤为重要。使用`BigInt`，整数溢出将不再是问题。
3. `null` 和 `undefined` 通常被认为是特殊值，这两种类型的值唯一，就是其本身。

## typeof null 返回什么？为什么？

typeof 返回的是 'Object' ，但是 null 却是一个基本类型，这其实是 JavaScript 本身的一个 bug ，应为在底层是通过二进制来表示不同的对象，前三位代表数据类型，如果全为 0 的话会被判定为 Object 类型，而null 的二进制全都是 0 ，前三位自然也是了，所以执行 typeof 的时候会返回 ‘Object’

想要搞清楚这个问题，我们首先要了解一下 JavaScript 数如何存储变量的， 我在 [JavaScript 的数据类型与操作符](https://app.gitbook.com/@1362061587/s/puddingmax/~/drafts/-MNIqw8qEn5HwsdcP9ZJ/javascript/javascript-de-shu-ju-lei-xing-yu-cao-zuo-fu)中提到过，变量分为**基本类型**和**引用类型**，基本类型是在_**栈内存存储一个新的变量**_，且对应一个新的值，而引用类型则是在_**堆内存中存储一个指针**_，指针的地址指向堆内存中的一个值

 所以，因为 {} 是一个对象，所以是一个引用类型，所以虽然创建了两个 {} ，但是他们是两个不同的对象，因为他们所**对应的地址不一样**

![](../.gitbook/assets/image%20%283%29.png)

\*\*\*\*

