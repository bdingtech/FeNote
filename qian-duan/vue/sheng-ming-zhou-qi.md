---
description: >-
  Vue
  在实例化的过程中会经过一系列的初始化，例如数据监听、编译模板、将实例挂载到DOM并且在数据变化时更新DOM，与此同时还会向外暴露出一些生命周期狗子，以方便开发者在不同的阶段添加自己定义代码
---

# 生命周期

## 一、初始化阶段

![&#x521D;&#x59CB;&#x5316;&#x9636;&#x6BB5;](../../.gitbook/assets/image%20%2885%29.png)

从 new Vue\(\) 到 create 之间的阶段叫做初始化阶段

这个阶段的主要目的是在Vue实例上**初始化**一些属性、事件及响应式数据，如 props、methods、data、computed、watch、provide 和 inject 等等

## 二、模板编译阶段

![](../../.gitbook/assets/image%20%2886%29.png)

这个阶段的主要任务是将模板编译为渲染函数

## 三、挂载阶段

![](../../.gitbook/assets/image%20%2880%29.png)

从beforeMount到mounted是挂载阶段、在这个阶段，Vue.js会将其实例挂载到DOM元素上，通俗来讲，**就是将模板渲染到指定的DOM元素中**，并且开启Watcher 持续的追踪依赖的变化。

在已挂载的状态下，Vue仍会持续的追踪状态变化，当数据（状态）发生变化时候，Watcher 会通知虚拟DOM重新渲染试图，并且会在渲染视图钱触发beforeUpdate钩子函数，渲染完毕后触发update钩子函数

## 四、卸载阶段

![&#x5378;&#x8F7D;&#x9636;&#x6BB5;](../../.gitbook/assets/image%20%2887%29.png)

应用调用vm.$destoroy方法后，生命周期会进入卸载阶段

在这个阶段，Vue.js会将自身从父组件删除，取消实例上所有以来的追踪并且移除所有的时间监听器

