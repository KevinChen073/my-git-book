关于前端工程相关的记录

### 工程主库

- webpack 4.0 (https://blog.csdn.net/qq_26733915/article/details/79446460)

### 工程相关
- json5格式：依赖编译过程，ES5对象语法的json文件格式：https://wxnacy.com/2018/02/18/json5/

### 工程工具
- grunt（2015前比较火）
- gulp（基本和grunt一起出现，后面pipe的写法优异，慢慢变火）
- webpack（打bundle想法盛行一时，感觉基本统治前端工程打包）

### 个人工作流提升
- Alfred（可视化编辑简易工作流）:[介绍文章](http://blog.surfacew.com/tool/2016/08/03/Alfred/)
- 油猴(tampermonkey):[介绍](https://tampermonkey.net/documentation.php?version=4.7&ext=dhdg&updated=true#_namespace)
- nw.js或者electron，给你创建一个跨前后端运行环境的工具
- bash：bash脚本，熟练掌握如alias\select等最简易脚本


### 详解
#### 油猴
油猴给我提供了一些在网站上的常用操作快捷方案。例如：
- 快速由某个链接生成二维码并且一直固定在页面
- 给你抢个票什么的
- 工作中自动挖掘页面中隐藏的html文本信息，并且展示出来（例如产品ID，网络服务机房号，IP地址，商家memberID，页面唯一标识码等，都有可能埋藏在html文档中，这时候用脚本把他们可视化展示出来，就可以省却很多排查时间）。

同时，油猴上一些已有的用户脚本也可以关注一下：例如[知乎回答](https://www.zhihu.com/question/22210090)

搜索已有的用户脚本网站：[Greasy Fork](https://greasyfork.org/zh-CN/scripts/24508-userscript-show-site-all-userjsz)