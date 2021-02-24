# 树

## 树是什么

Js中没有树，但是可以用Object和Array构建树

树的常用操作：深度/广度优先**搜索**、先中后**遍历**

```javascript
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

```javascript
{
    value:'zhejiang',
    label:'zhejiang',
    children:[
        {
            value:'hangzhou',
            label:'hangzhou',
            children:[
                vaule:'xihu',
                label:'west Lake'
            ]
        }
    ]
}
```

## 深度优先搜索 \(Depth-First-Search，DFS\)

深度优先，就好像看书一样，是直接把第一章看完然后再看第二章

![&#x6DF1;&#x5EA6;&#x4F18;&#x5148;&#x904D;&#x5386;](../../../.gitbook/assets/image%20%2862%29.png)

### 代码实现

```javascript
const tree1 = {
  val: "a",
  children: [
    {
      val: "b",
      children: [
        {
          val: "d",
          children: [],
        },
        {
          val: "e",
          children: [],
        },
      ],
    },
    {
      val: "c",
      children: [
        {
          val: "f",
          children: [],
        },
        {
          val: "g",
          children: [],
        },
      ],
    },
  ],
};

function dfs(tree) {
  console.log(tree.val);
  tree.children.forEach((item) => {
    dfs(item);
  });
}
dfs(tree1);
```

## 广度优先搜索\(Breadth-First-Search\)

顾名思义，广度优先，注重的是广度，也就是先看目录然后再一章一章的看

![&#x5E7F;&#x5EA6;&#x4F18;&#x5148;&#x904D;&#x5386;](../../../.gitbook/assets/image%20%2861%29.png)

### 代码实现

基本思路

1. 建立一个队列，先把根节点入队
2. 然后再将根节点出队
3. 将children节点依次入队
4. 重复2、3步直到队列为空

```javascript
function bfs(tree){
    let queue = []
    queue.push(tree)
    while(queue.length > 0){
        //根节点出队
        let n = queue.shift()
        console.log(n.val)
        //children节点入队
        n.children.forEach(item => {
            queue.push(item)
        })
    }
}
```



