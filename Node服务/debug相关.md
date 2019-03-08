
# node的debug相关方案

### console.log
不说了

### debug模块

```javascript
const debugLog = require('debug')('xingxiao');
debugLog('xxxx');
```
运行时：
```bash
DEBUG=xingxiao tnpm run dev
```

这样的话，就能够在控制台只打我的debug参数了.

### 环境注入方案
根据不同的环境判断本地是什么，然后再看要不要打log.[node的env](https://cnodejs.org/topic/57a409657a922d6f358cd22d)
```javascript
// vscode的launch.json配置
{
    "env": {
        "NODE_ENV": "development",
        "DEBUG_ENV": "local-debug"
    },
}
const isLocalDebug = process.env.DEBUG_ENV === 'local-debug';
```

### logger
打日志

### final
结合环境注入，封装一个logger。这个logger会根据不同环境（本地，开发，预发，线上）。调用不同的模块打出数据。
例如：
- 本地：console.log（控制台）
- 单独模块：debugLog
- 线上：ctx.logger（日志文件）