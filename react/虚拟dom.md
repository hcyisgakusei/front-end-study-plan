## 前言

前端通常我们渲染一个html有两种方式，第一种是将整个节点替换，第二种就是指操作我们需要更新的那一部分。

对于第一种，整个节点替换，这会导致浏览器的回流和重绘，如果只是一小部分可能还不是特别明显，如果对大一点dom这样操作，性能影响就非常大的，
但是这样也有一个好处就是代码可以统一用一套。

对于第二种，只修改变化的一部分，这就解决了第一种带来的性能问题，但是又会造成另外一个问题，我们需要对每一个中操作都封装一遍特定的方法，
在庞大的系统这种，代码就会变得异常难维护。

## Virtual Dom

react 使用的 Virtual Dom 技术就是为了很好的解决上面两个问题，我们可以用一种统一的方式去渲染html又不会对性能有很大的影响。

### 流程

- 在初始化 react 对象的时候，react 会初始化一个虚拟树
- 接着react 会根据这颗虚拟树实例化出真实树，并将树挂载到指定的dom节点上
- 后面每当react 的状态改变的时候，react 都会重新生成一颗虚拟树
- 然后比较老的和新的虚拟树的区别，提取出需要修改的部分来修改真实树

### diff 算法

为了让时间复杂度尽可能的小，react 之比较同层的树的差异，因为在实践过程中跨层级的操作dom还是比较少见的。
在比较的时候，react 会把不同的部分记录下来。

### 把差异渲染出来

最后 react 会把记录下来的差异部分渲染出来，具体会根据不同的差异类型做不同的操作。例如：替换，重新排序，props变化，text变化等

### virtual dom 带来的好处

#### 1. 组件的高度抽象化

利用 babel 编译 jsx 我们能够声明式的书写 html，在 javascript 中书写 html，小粒度的复用我们的这些 "html"

#### 2. 可以更好的实现 SSR，同构渲染等

#### 3. 框架跨平台


