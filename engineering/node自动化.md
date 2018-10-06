## node自动化相关

- 流
- commandar
- process
- 相关查询能力
- 执行系统能力
- 文件能力


### process
用于处理进程相关，可以依靠其底层的API来进行人机交互
#### argv
全局变量process，关于nodejs运行时
``` javascript
let args = process.argv;
console.log(args);
// 输出node运行目录以及js目录以及用户输入的额外参数
// output: ["/usr/local/bin/node", "/myOwnFile/myTestWebpack/demo1/demoProcess.js"]
```

#### 其他process
- pid
- cwd
- uptime
- stdin\stdout

### 相关查询和处理库

#### querystring
用于处理url参数相关

#### url
用于处理url相关

#### os
用于获取当前系统相关信息，包括:
- homeDir() home目录
- platform() 操作系统
- cpus() cpus多核等信息

### open
#### 创建子进程
``` javascript
const { exec, fork, execFile, spawn } = require('child_process');
```
> Node allows you to create a child process in four different ways: spawn, fork, exec and execFile.
- spawn 可带参数，并且流式返回返回值
- fork 允许父进程和子进程之间进行交互
- exec 可带参数，一次那行执行后返回
- execFile 不在shell中创建，直接运行一个新文件

#### start和open
``` javascript
const WINDOWS_PLATFORM = 'win32';
let command;
if (osPlatform === WINDOWS_PLATFORM) {
    command = `start microsoft-edge:${url}`;
} else {
    command = `open -a "Google Chrome" ${url}`;
}
```

### FileSystem