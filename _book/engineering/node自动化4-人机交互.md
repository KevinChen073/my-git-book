
## 和用户进行交互
### 基础
一般而言，我们直接使用process.argv获取第三个以后的参数即可
``` javascript
let args = process.argv;
console.log(args);
// 输出node运行目录以及js目录以及用户输入的额外参数
// output: ["/usr/local/bin/node", "/myOwnFile/myTestWebpack/demo1/demoProcess.js"]
```

### better的方法
但如果我们的argv是使用--a=b的方式的，那么用基础方式解读未免有些麻烦。那么这时候就可以使用库帮忙
[`minimist`库](https://www.npmjs.com/package/minimist):parse argument options

### question
用于进行一问一答的人机交互。（基于process.stdin和stdout）

[readline-sync](https://www.npmjs.com/package/readline-sync)
- keyIn
- keyInSelect
- keyInYN
- question
``` javascript
var readlineSync = require('readline-sync');
```

### commander
用于脚手架的一个问答和配置库:https://www.npmjs.com/package/commander

demo如下：
``` javascript
const nobot = require('commander');
const { version } = require('../package');
// commands
const setup = require('./commands/setup');
const game = require('./commands/game');
const template = require('./commands/template');
nobot
 .version(version);
nobot
 .command('setup')
 .description('clone repository dependencies')
 .action(setup);
nobot
 .command('game <ticketId> [otherMsg]')
 .description('create and deploy a new game reskin')
 .options('-h, --help')
 .action(game);
nobot
 .command('template')
 .description('release core files of template')
 .option('-i, --id, [id]', 'what template to release')
 .action(template);
nobot
 .command('*')
 .action(() => nobot.help());
nobot.parse(process.argv);
if (!process.argv.slice(2).length) {
 nobot.help();
}
```

处理函数如下：
```javascript
function game(ticketId, otherMsg, options) {
    if (options.help) {
        // do something....
    }
}
```

### 其他库
- grunt：通过prompt这个库来实现，点击 传送门
- yo：通过Inquirer.js这个库来实现，点击传送门
实现这种：
![](https://segmentfault.com/img/bVCJ0f)