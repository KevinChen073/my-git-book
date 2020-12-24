<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2020-12-22 19:02:15
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/MVVM/vue&react.md
-->
# Vue和React的一些对比

- 数据绑定的差别：vue的数据劫持defineProperity\\react的vdom单向数据流动
- vdom：vue2后，vdom的想法也已经用进去了，就性能而言，也差不了多少

### 生态
#### react
- redux\dva \\ vuex - 分离UI和逻辑，视图组件只需要负责渲染，逻辑控制负责控制。
- react-router \\ vue-router
- react-native \\ weex用的也是vue

### 生命周期
- react: constructor -> willMount -> render -> DidMount -> willReceiveProps -> shouldComponentUpdate -> willUpdate -> render -> DidUpdate -> willUnmount -> didUnmount
- vue: create -> beforeMount -> render -> mounted -> beforeUpdate -> updated -> beforeDestory -> destoryed

- 父子组件，都是在render中进行下一个
- 继承组件，React用的是 ES6 的class继承，但是Vue是继承了生命周期（更像是父组件）

### 内部数据流
- react: state和props
- vue: data

### 钩子hook
参考示例：https://github.com/streamich/react-use
解决复用、层层嵌套的问题，改为函数组件做有状态的事情。（https://segmentfault.com/a/1190000016953180）（https://zhuanlan.zhihu.com/p/50274018）
- vue的hook
- react的hook（https://www.cnblogs.com/qcloud1001/p/9930781.html）

### 骚气用法
- 高阶组件：高阶组件和高阶函数。（http://hcysun.me/2018/01/05/%E6%8E%A2%E7%B4%A2Vue%E9%AB%98%E9%98%B6%E7%BB%84%E4%BB%B6/）。vue在最终解析的时候，其实是一个对象。vue中更倾向于使用mixin（https://segmentfault.com/a/1190000000360485）
- 继承：原型链上的继承，相关属性会先调用父组件，再调用子组件。而React则是重写的方式。
- 模板：template和JSX

#### 两者对比
React、Vue之间的关系
早期会有点不同，到了现在基本上能力和原理都一致。好处在于Vue在国内受众广，上手难度低。React背靠Facebook整体来说会更创新一点。
底层实现和原理
MVVM的一套框架，进行了数据与UI的绑定，让我们关注在数据逻辑上，忽略UI。早期两者实现很不一样。React有一些创新：VDom、diff、JSX。双向绑定方案：setState、DefineProperity、Proxy。React 16后有hooks等。到了后期大家都底层原理接近一致。

中层配套方案
Redux、dva、React Router等，社区有很多配套方案。并且针对React的生命周期进行优化都有。

对外社区
两者的社区

#### hooks的实现
