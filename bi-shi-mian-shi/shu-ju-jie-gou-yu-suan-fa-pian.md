---
description: 数据结构和算法是每个工程师都应该具备的基本技能，但是这一块的学习曲线可能比较长，所以要持续不断的学习与总结，量变产生质变
---

# 数据结构与算法篇

## 排序算法

### 例题

给你一个整数数组 `nums`，请你将该数组升序排列。

示例 1：

```text
输入：nums = [5,2,3,1] 
输出：[1,2,3,5]
```

 示例 2：

```text
输入：nums = [5,1,1,2,0,0]
输出：[0,0,1,1,2,5]
```

### 冒泡排序

基本思想是通过相邻元素的两两比对，不断的将较大或者较小的元素前移动或者后移，从而实现升序或者降序

![](https://user-gold-cdn.xitu.io/2018/8/14/16538fc898b4742e?imageslim)

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function(nums) {
    for(let i = 0; i < nums.length; i++){
        for(let j = 0; j <nums.length - i; j++){
            if(nums[j] > nums[j+1]){
                let temp = nums[j]
                nums[j] = nums[j+1]
                nums[j+1] = temp
            }
        }
    }
    return nums
};
```

### 选择排序

选择排序的思想就是不断选择最小的数，然后把他拎到最前面，最后的出来的就是有序的数列

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function(nums) {
    //选择排序
    for(let i = 0; i < nums.length; i++){
        for(let j = i + 1; j < nums.length; j++){
            //如果后面的值比第一个值小，则交换
            if(nums[j] < nums[i]){
                let temp = nums[j]
                nums[j] = nums[i]
                nums[i] = temp
            }
        }
    }
    return nums
};
```

### 插入排序

插入排序的思想和打扑克时差不多，我们会依次调整牌的顺序，抽出一张牌，然后按照大小顺序放回去

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortArray = function(nums) {
    //外循环从1开始，默认nums[0]是有序段
    for(let i = 1; i < nums.length; i++){
        for(let j = i; i > 0; j--){
            if(nums[j] < nums[j-1]){
                [nums[j-1],nums[j]] = [nums[j],nums[j-1]]
            }else{
                break
            }
        }
    }
    return nums
};
```

### **时间复杂度**

乍一看，好像插入排序速度还不慢，但是要知道： 当序列正好逆序的时候，每次插入都要一次次交换，这个速度和冒泡排序是一样的，时间复杂度O\(n²\)； 当然运气好，前面是有序的，那时间复杂度就只有O\(n\)了，直接插入即可。

| 排序算法 | 平均时间复杂度 | 最坏时间复杂度 | 空间复杂度 | 是否稳定 |
| :--- | :--- | :--- | :--- | :--- |
| 冒泡排序 | O\(n²\) | O\(n²\) | O\(1\) | 是 |
| 选择排序 | O\(n²\) | O\(n²\) | O\(1\) | 不是 |
| 直接插入排序 | O\(n²\) | O\(n²\) | O\(1\) | 是 |

好了，这张表如何快速记忆呢？ 方法就是一开始写的**基本排序算法** 。 一开始就说到，基本思想就是两层循环嵌套，第一遍找元素O\(n\),第二遍找位置O\(n\)，所以这几种方法，时间复杂度就可以这么简便记忆啦!

## 参考资料

1. \*\*\*\*[**前端笔试&面试爬坑系列---算法**](https://juejin.cn/post/6844903656865677326#heading-3)\*\*\*\*



