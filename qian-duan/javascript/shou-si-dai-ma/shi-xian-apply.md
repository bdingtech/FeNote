# 实现 apply

过程和 call 类似，这里就不在赘述

```javascript

Function.prototype.myApplay = function (obj, arr) {
  let key = Symbol();
  let result;
  obj = obj || window;
  obj[key] = this;
  //处理异常
  if (!arr) {
    result = obj[key]();
  } else {
    result = obj[key](...arr);
  }
  delete obj[key];
  return result;
};
```

