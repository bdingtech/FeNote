# JS刷题总结

```javascript
// 使用箭头函数缩减代码
// 处理输入，可以用.map，需要注意其所有参数
// 此外其他迭代方法也需要掌握。
let line = readline().split(' ');
line = line.map((e) => parseInt(e));

// 去重
arr = [...new Set(arr)];
// 升序,排序可以用sort，默认是字典序,并且可以根据需要定制，需要深入掌握
arr.sort((a, b) => a - b);
// 迭代输出
arr.forEach((i) => console.log(i));
// 求最大值，使用扩展运算符...
max = Math.max.call(...arr);
// 复制数组
arr2 = [...arr1];
arr2 = arr.concat();
arr2 = arr.slice();

// 善用解构
// 变量赋值
let [a, b, c, d, e] = [1, 2, 3, 4, 5]; // a=1,b=2,c=3,d=4,e=5
// 交换变量值
[a, b] = [b, a];

// 题外话：字符串中的字符是无法交换的
let str = 'ab';
[str[0], str[1]] = [str[1], str[0]]; // 无效，"ab"
// 不过可以将字符串拆成字符数组后就可以交换了
str = str.split(''); // ["a","b"]
[str[0], str[1]] = [str[1], str[0]]; // ["b","a"]

```



