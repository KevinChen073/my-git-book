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

### ES7+
generator
async\await