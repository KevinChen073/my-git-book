<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2020-12-24 00:44:15
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/mvvm.md
-->

列举下现代常见的MVVM框架及其发展编年史

- React
- Vue
- Angular
- Backbone

### 现状分析
[2018年JavaScript现状报告](https://www.cnblogs.com/peiyu1988/p/9317182.html)
|                                | 公司           | 现状       | 版本对比                                                   | 趋势 | 个人使用感觉                                                 | 数据绑定机制                                                 |
| ------------------------------ | -------------- | ---------- | ---------------------------------------------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Angular](https://angular.io/) | Google         | Angular4   | ng2和TypeScript结合，且更关注客户端。ng4出力于服务端渲染。 |      | Angular更偏向于企业级应用。其API设计更倾向后端思想（MVC模式，为每个功能提出一个概念），配合组件化。学习曲线陡，但应用于大团队中间件协作会有好处。 | ng1\ng2事件绑定脏检查.ng2的zone.js通过闭包提供伪造的上下文用于检查 |
| React                          | Facebook       | React 16.0 | 社区强大，文档获取方便。                                   |      | React率先提出vdom概念，其vdom概念也可以移植到其他领域，如RN，WEEX(Rax)。主要为组件化、单向数据流动。而且社区、生态、以及业界用得都比较多。最重要一点是……文档不用翻墙。 | 单向数据流动diff                                             |
| Vue                            | 个人（尤雨溪） | Vue2       | 上手容易，语法简单                                         |      | Vue感觉就是MVVM时代的jQuery，上手简单。Vue2后也吸收了vdom等理念。感觉用于个人项目挺好，但是大型协作项目用vue则需要很强的代码规范去制约。 | 数据劫持defineProperity                                      |


### 三者数据绑定的对比
绑定的方案：
1. 能通过固定的接口才能改变变量的值，比如说只能通过set()设置变量的值，set被调用的时候比较一下就知道了。这种方法的缺点是写法比较繁琐。（如vue的思路）
2. 脏检查，将原对象复制一份快照，在某个时间，比较现在对象与快照的值，如果不一样就表明发生了变化，这个策略要保留两份变量，而且要遍历对象，比较每个属性，这样会有一定的性能问题（ng的思路）

#### Angular1
脏值检查，对原生事件、异步事件需要用$apply来检查.
> angular使用的就是脏检查：
1. 不会脏检查所有的对象。当对象被绑定到html中后，这个对象才会添加为检查对象（watcher）
2. 不会脏检查所有的属性，同样当属性被绑定后，这个属性才会被列为检查的属性
> 在angular程序初始化时，会将绑定的对象的属性添加为监听对象（watcher），也就是说一个对象绑定了N个属性，就会添加N个watcher。
> angular什么时候去脏检查呢？angular所系统的方法中都会触发比较事件，比如：controller初始化的时候，所有以ng-开头的事件爱你执行后，都会出发脏检查。必要的时候我们要手动的触发脏检查：$apply仅仅只是进入angular context，然后通过$digest触发脏检查

#### Angular2
[脏值检查 Zone](https://blog.csdn.net/u010977147/article/details/53785733)覆盖了原生的事件（如setTimeout、Promise、EventListener），达到在数据更改时对UI的改动不需要手动调用。

#### vue 
数据劫持defineProperity：解决从data -> view
订阅-发布模式，给输入控件绑定事件: 解决从view -> data
https://www.cnblogs.com/libin-1/p/6893712.html

#### Vue2
数据绑定方式没变，但是加上了React的vdom思路使得数据diff性能更高
另外，取消了如$boardcase\$dispatch等跨组件调用的能力。取而代之的是建议使用事件管理器和单项数据流层redux的思路

#### React 
单向数据流动，React结合了脏检查以及固定接口改变，只有在调用固定接口setState的时候，会对整体进行一次渲染。但是这个渲染又是在vdom层面经过了一次diff的，只有对真正需要改动的地方才会操作html DOM。

#### 反应式编程
在服务器上对数据变化立即反馈，提高CPU的使用。创建一个可观测的对象。当对象变化时，立即触发相关函数。
```javascript 
var observer=Rx.Observer.create({a:'b',c:"d"});
observable.subscribe(observer, ()=>{});
```