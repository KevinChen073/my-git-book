dva:https://dvajs.com/guide/
因为要接触深层次业务开发，业务状态过多，因此需要单向数据流流动方案。项目选型dva，目前了解一下dva是什么

- elm 概念，通过 reducers, effects 和 subscriptions 组织 model（约定>配置）

## 能力集成
- react
- react-router
- redux
- redux-saga：处理异步的redux：https://github.com/redux-saga/redux-saga
- Subscriptions：收集其他源（例如键盘输入、鼠标动作等）

## react等关系
https://dvajs.com/guide/fig-show.html#%E5%9B%BE%E8%A7%A3%E4%B8%80-react-%E8%A1%A8%E7%A4%BA%E6%B3%95
UI和逻辑分离：（纯函数方式）
> React 官方指导意见, 如果多个 Component 之间要发生交互, 那么状态(即: 数据)就维护在这些 Component 的最小公约父节点上, 也即是 <App/>
> <TodoList/> <Todo/> 以及<AddTodoBtn/> 本身不维持任何 state, 完全由父节点<App/> 传入 props 以决定其展现, 是一个纯函数的存在形式, 即: Pure Component

## 个人思路
Q：react的官方解释是希望所有的state由父组件控制，而子组件内部不负责state的维护。但实际操作中，往往子组件会维护自己的state。因为业务组件相对独立，导致组件不止负责UI，还会负责逻辑。
A：但对一个项目而言，组件应该足够抽象。而业务逻辑由最小独立的父组件控制。

Q:按照dva的说明，redux做的是UI和逻辑分离开来，而其中UI触发数据变更以及数据注入UI则是通过dispatch和connect来进行，而不是通过dispatch后由上层父组件逐步传下来数据（慢，而且处理的数据会很多）
A：http://taobaofed.org/blog/2016/08/18/react-redux-connect/。redux使用了provider和connect方案来解决。provider为最外层接受state的组件，而需要使用state的子组件则通过connect来获取相关的数据。

Q:为了确保每次操作state都只会在dispatch中进行，因此需要state是一个不可变对象。
A:每次都是一个新的对象，保证内部修改state的时候不会影响下一次的state。

Q:reducer的概念
A：因为redux中，UI和逻辑完全分离，则UI不需要关注state。因此有一个stateProps的概念（即每次变化，在connect中都把state和props根据一定计算返回成一个数据），以props的方式传给UI组件

## redux-saga和thunk的差别
参考文章：https://www.jianshu.com/p/ec2d93cf70b3
saga使用put和call来做一个，Promise版的dispatch和fetch（并且在结束后调用下一个next）