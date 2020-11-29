---
description: 这类引用类型所导致的看起来魔幻的问题一直困扰着很多新人
---

# 为什么 {} !== {} ?

想要搞清楚这个问题，我们首先要了解一下 JavaScript 数如何存储变量的， 我在 [JavaScript 的数据类型与操作符](https://app.gitbook.com/@1362061587/s/puddingmax/~/drafts/-MNIqw8qEn5HwsdcP9ZJ/javascript/javascript-de-shu-ju-lei-xing-yu-cao-zuo-fu)中提到过，变量分为**基本类型**和**引用类型**，基本类型是在_**栈内存存储一个新的变量**_，且对应一个新的值，而引用类型则是在_**堆内存中存储一个指针**_，指针的地址指向堆内存中的一个值

 所以，因为 {} 是一个对象，所以是一个引用类型，所以虽然创建了两个 {} ，但是他们是两个不同的对象，因为他们所**对应的地址不一样**

![](../.gitbook/assets/image%20%283%29.png)

\*\*\*\*

####  

