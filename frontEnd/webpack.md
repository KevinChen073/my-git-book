<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2020-12-24 00:46:09
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/webpack.md
-->
# webpack相关
### 关于使用等教程
这里就不写啦，毕竟已经有这么多的相关教程。
四大概念：input、output、plugin、loaders
参考阮老师的就行：https://github.com/ruanyf/webpack-demos#demo01-entry-file-source

### webpack的主要能力

- 提取公共模块：按模块提取代码
- 代码分割（懒加载）：通过特殊写法来自定义代码拆分点
- Tree shaking
- 混淆压缩
- 热更新
- 预编译语言：典型如，babel loader、sass\less loader
- 其他资源处理：css loader、image loader

### 相关思考
- Css loader，css in js（利弊减少建联，但是css依赖js，无法同构输出）
- 工程化：上手 开发 编译 调试 发布 监控
- webpack.optimize的自带模块

### 代码分割（懒加载）
自己话概括一下：通过特殊写法来自定义代码拆分点，从而最终生成多份bundle，并且对除最需要bundle外都进行动态加载。参考这篇掘金就很好：https://juejin.im/post/5a6d7eeef265da3e4d72f1f9

因为是用于性能优化的，如果在实际使用上，可能要考虑这么几点：
1. 【加载在无线优化上】webpack本体用的script标签添加，那么必须要考虑的是建联问题。毕竟在无线下，网络情况始终是一个问题。另一个思路是如果在hybrid中则使用无线客户端的辅助能力，例如可以让客户端配置提前加载某些模块或者缓存到本地。而在纯浏览器上则使用service worker代替。
2. 【构建中的公共模块抽离】如果构建出的子模块中公共模块还需要再打包一次，那么就很浪费体积了。
3. 【写法上异步又变多了】写法上多用异步，肯定会对开发者很不友好，这部分建议通过构建对开发者透明化去解决。

### Tree shaking
参考这几篇：
[你的ts真的有用吗](https://juejin.im/post/5a5652d8f265da3e497ff3de)
[ts原理分析](https://juejin.im/post/5a4dc842518825698e7279a9)

对打包模块中没有被使用的模块shake掉，考虑这么几点
1. webpack或者rollup自带的shaking，其实是文件内的块shaking，分析文件里面的代码流。然后剔除没有被使用的代码。但需要注意的是，如果产生了副作用（例如引用修改外部变量、class的严格bable编译）都会造成shaking的失败。
2. 如果是通过模块的写法来规定，例如一个大模块里面有N个小的子模块。构建bundle的时候再把没有被引用的子模块干掉，这种方式会比较适合。也类似于antd的构建出N个小文件让用户引用。

### AST语法树分析
对语法树分析进行处理
- 例如对某个if逻辑下的分支全部处理掉
- 例如对某个特殊语法进行替换