## node自动化相关

- 流
- commandar
- process


### process
全局变量process，关于nodejs运行时
``` javascript
let args = process.argv;
console.log(args);
// 输出node运行目录以及js目录以及用户输入的额外参数
// output: ["/usr/local/bin/node", "/myOwnFile/myTestWebpack/demo1/demoProcess.js"]
```