<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2020-12-27 15:09:45
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/preformance.md
-->
性能优化相关

### 通用Web性能优化
- 通过Service Worker：预加载和cache
- JS阻塞性：基于微任务和宏任务，在CSR渲染方案中，异步JS也要空闲时执行
- HTML解析优化

### 无线性能优化
#### 基于CSR路径
- Native路由优化
- 静态资源下载
- 接口优化
- 渲染优化
- 极限优化

### Native跨端性能优化
- 前端语言编写Native：小程序、RN、WEEX
- Native缓存 cache
- Native预加载 prefetch
- Native支持的组件拆分下载
- QuickJS（JSCore级别的优化，从JS解析变成直接执行字节码）

### 业界方案性能优化
- Google的AMP、PWA项目
- WKWebview
- 腾讯的内核方案、U4浏览器内核（多进程、可定制JSCore、混合渲染、兼容性问题减少、JS执行加快，光栅化加快）
- Amazon的全投入SPA应用
- 分析工具：LightHouse
