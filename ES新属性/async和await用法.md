SF上这篇不错：https://segmentfault.com/a/1190000007535316
阮一峰老师的：http://www.ruanyifeng.com/blog/2015/05/async.html

## async和await

基于Promise的语法糖……又是语法糖。
- async用于生命一个函数是异步函数，这样，这个函数一般会返回Promise.resolve()
- await为async wait的缩写，用于等待某个值或者Promise.resolve返回值。并且如果是Promise.resolve，会阻塞后续进程。（当然，这个进程是在Promise中阻塞的，这就是为什么await需要在async里面去使用）

## Promise、generator、async\await的优劣
不可否认，三者都是为了使得异步编程同步化而做的事情。并且他们也没办法使得异步编程直接同步化，只是能够使得异步编程的写法更加优雅而已。
Promise: 回调到Promise.then的链式调用
async\await:从链式调用到await 同步写法。Promise 方案的死穴—— 参数传递太麻烦
generator：从链式调用到next的迭代器写法

> async 函数就是 Generator 函数的语法糖。并且
- await支持非Promise类型返回
- 自带执行器，不需要搞个Q之类的库（promise.resolve以后再调用下一个next)
- 语义清晰

当然，如果这个async函数还是需要return值，那么就是return一个promise啦，直接then或者继续包在async\await里面即可
## 示例
``` javascript
var all = Q.async(function* () {
    var src = yield getData(); // 一个异步promise
    var img = yield getImg(src); // 又一个异步promise
    var d = getImgSync(src); // 同步的函数
    showImg(img);
});

all();
```

``` javascript
async function all() {
    var src = await getData(); // 一个异步promise
    var img = await getImg(src); // 又一个异步promise
    var d = await getImgSync(src); // 同步的函数，也可以用await
    showImg(img);
}

all();
```