# 画一个三角形、梯形、扇形、圆形、椭圆？

## 三角形

### 模板

利用元素的 border 绘制三角形，先来看一下宽高均为 0，border 有宽度的效果是啥样的：

```css
.tiangle{
    width: 0;
    height: 0;
    border-top: 100px solid #f00;
    border-right: 100px solid #0f0;
    border-bottom: 100px solid #00f;
    border-left: 100px solid #ff0;
}
```

![](../.gitbook/assets/image%20%2836%29.png)

然后我们可以通过给任意三边的颜色设置为 `transparent` 即可分别实现任一方向的三角形。

### 普通三角形

```css
.tiangle{
    width: 0;
    height: 0;
    border: 100px solid transparent;
    border-bottom: 100px solid #00f;
}
```

![](../.gitbook/assets/image%20%2830%29.png)

### 等边三角形

```css
.tiangle{
    width: 0;
    height: 0;
    border: 100px solid transparent;
    border-bottom: 200px solid #00f;
}
```

![](../.gitbook/assets/image%20%2833%29.png)

### 倒三角形

```css
    .tiangle{
        width: 0;
        height: 0;
        border: 100px solid transparent;
        border-top: 200px solid #00f;
    }
```

![](../.gitbook/assets/image%20%2832%29.png)

## 梯形

和三角形一样，通过三边设置为透明则可以得到相应的图形

### 模板

```css
  .tiangle {
    width: 50px;
    height: 50px;
    background: #ff0;
    border-top: 50px solid #f00;
    border-bottom: 50px solid #00f;
    border-left: 50px solid #0f0;
    border-right: 50px solid #0ff;
}
```

![](../.gitbook/assets/image%20%2839%29.png)

### 普通梯形

```css
  .tiangle {
    width: 50px;
    height: 50px;
    border: 50px solid transparent;
    border-bottom: 50px solid #00f;
  }
```

![](../.gitbook/assets/image%20%2838%29.png)

## 扇形

### 模板

```css
  .tiangle {
    width: 0px;
    height: 0px;
    background: #ff0;
    border-radius: 100px;
    border-top: 100px solid #f00;
    border-bottom: 100px solid #00f;
    border-left: 100px solid #0f0;
    border-right: 100px solid #0ff;
  }
```

![](../.gitbook/assets/image%20%2841%29.png)

### 普通扇形（利用border-radius）

```css
  .tiangle {
    width: 100px;
    height: 100px;
    border-radius: 100px 0 0;
    background-color: wheat;
  }
```

![](../.gitbook/assets/image%20%2835%29.png)

### 普通扇形（利用border）

```css
  .tiangle {
    width: 0px;
    height: 0px;
    border-radius: 100px;
    border: 100px solid transparent;
    border-top: 100px solid wheat;
  }
```

![](../.gitbook/assets/image%20%2834%29.png)

## 圆形

```css
.tiangle {
  width: 100px;
  height: 100px;
  border-radius: 100px;
  background-color: wheat;
}
```

![](../.gitbook/assets/image%20%2837%29.png)

## 椭圆

椭圆依旧依赖 `border-radius` 属性，很多人应该都没注意过，border-radius 其实可以设置水平半径和垂直半径两个值 ，[参考MDN - border-radius](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius),具体用法为 `border-radius: 水平半径 / 垂直半径;`.

![](../.gitbook/assets/image%20%2831%29.png)

```css
  .tiangle {
    width: 200px;
    height: 100px;
    border-radius:  200px / 100px;
    background-color: wheat;
  }
```

![](../.gitbook/assets/image%20%2840%29.png)

