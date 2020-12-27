<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2020-12-24 00:14:12
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/javascript.md
-->
关于JS语言集的问题

### ES5

### ES6
ES6还是看阮一峰吧~ http://es6.ruanyifeng.com/#docs/proxy
- 函数语法糖：()=>{}，普通函数+作用域绑定。如下：
```
var opt = {
    name:"Amy",
    name2: this.name,
    say:function(){
        return this.name;
    },
    say2:function(){
        setTimeout(function(){
            console.log(this.name);
        })
    },
    say3:function(){
        setTimeout(() => {
            console.log(this.name);
        })
    }
}

console.log(opt.name2); //1. 这里打印出什么？undefined
console.log(opt.say); //2. 这里打印出什么？  function() {return this.name}
opt.say2(); //3. 这里打印出什么？			 undefined
opt.say3(); //4. 这里打印出什么？			 'Amy'
var k = {a:2,b:this, c: ()=>{return this},d: function(){return this}}
undefined
k.c()
Window {postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, frames: Window, …}
k.d()
{a: 2, b: Window, c: ƒ, d: ƒ}
```

- Proxy代理
- let\const等声明
- 新的类型，如Set、Map等。Set是无重复对象的Array，更像是一颗树的实现，而Array是队列。Map是键值对，只是键不仅是stirng了，引用。


### ES7+
generator
async\await

### ES2020
- 可选链式，TS很像
- Dynamic import。webpack5中有这个特性
- globalThis。Node、Weex等非浏览器环境
- bigInt。大数字