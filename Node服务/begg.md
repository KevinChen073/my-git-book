## 这里记录一些begg的使用情况
http://begg.alibaba-inc.com/zh-cn/core/development.html#%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE-2

### 概况
这是一个后端服务框架，区别于express（使用connect中间件），egg基于koa，使用的是co中间件（免得回调太多）的概念
koa和express的对比：https://juejin.im/entry/58a11f61128fe1005823a257

#### 中间件的种类
- 插件级：启动某个中间件引致再调用其他中间件
- 应用级：应用启动就调用中间件
- 路由级：根据路由去调用不同中间件

#### 中间件执行顺序
中间件执行顺序都是注册先后顺序啦。

#### 中间件机制
- express：一系列线性的中间件执行。并且通过next把控制权移交给下一个。。https://www.jianshu.com/p/2744ad87fc92、https://expressjs.com/zh-cn/guide/using-middleware.html
> 在 Express 中，你必须在调用 next() 和发送 response 两个做法中二选一——否则请求永远不会完成。

---
- koa：一个洋葱圈的方式。await next把控制权移交到下一级中间件，再慢慢回到外部。https://hijiangtao.github.io/2017/11/10/Mastering-Koa-Middleware/
> koa基于Promise,async或者generator

### begg日志和调试
- 日志 -> logger模块，会根据config配置打到不同地方，但为什么搜索不到啊……
- 调试 -> egg-bin debug或者是直接使用debug这个npm模块。两者的优劣(https://www.npmjs.com/package/debug)
- console.log ，不提了
- vscode的debug方式