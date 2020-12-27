<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-27 15:10:19
 * @LastEditTime: 2020-12-27 22:01:52
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/Event Loop.md
-->
# EventLoop
浏览器、Node内的JS都是单进程的。但是在此之外我们还会有异步操作，例如Promise、Timeout、网络IO、本地IO、跨进程通讯等。在这之中，多个任务是如何进行的，这就是EventLoop研究的内容

## ⏰每一个JS文件或者是一个Script都是一次事件Loop
针对浏览器内，第一次宏任务可以理解为html下载下来时的第一次执行。
HTML的执行可以视为单独的一次宏任务。如果其中有任务是宏任务，有可能会被阻塞。可能有其他宏任务插入，例如script回来了或者setTimeout到期
```html
<body>

    <script>
    const sleep = (times = 1)=>{
        const sDate = Date.now();
        let c = 0;
        do{
            c++
        }while(c < 1e8 * times);
        console.log('sleep time', Date.now()-sDate );
    } // 约75ms
    const biz1 = ()=>{
        console.log('biz1:', Date.now());
    };
    const biz2 = ()=>{
        console.log('biz2:', Date.now());
    };

    
    console.log('time0:', Date.now());
    setTimeout(()=>{
        console.log('远程数据开始执行:');
        console.log('执行任务,sleep');
        sleep(1);
        console.log('远程数据开始完成:');
    }, 100);
    </script>
    
    <script>
    setTimeout(biz1);
    sleep(3); // 等75ms
    </script>
    <script>
    setTimeout(biz2);
    </script>
</body>
```
因为每个script都是一个单独的宏任务，所以就导致了时序不是time1 -> time2 -> sleep，而是time1->sleep->time2。这也是一个前端常见的首屏打开优化项，防止JS进程被阻塞。

## 🏡异步任务有宏任务和微任务
- `Promise`、`setMicroQueue`都是微任务
- async\await的底层实现就是Promise，所以也是微任务
- `setTimeout`等都是宏任务
- 🌰`new Promise()`中的内容是同步执行的！！
基本一次Loop的顺序是：
同步执行宏任务（同步执行内容） -> 微任务 -> 下一个宏任务 -> 无宏任务（完结）。因此在作者给出的例子中
```javascript
setTimeout(() => alert("timeout"));

Promise.resolve((resolve)=>{
    alert('code1');
    resolve();
}).then(() => alert("promise"));

alert("code2");
```
顺序是code1（同步执行1）、code2（同步执行2）、promise（微任务microTask）、timeout（下一个宏任务macroTask)

## 🤔兼容问题：CanIUse
- Chrome > 33
- Safari > 7.1
但是面对低于这些版本的浏览器，没有原生的Promise支持，自然也没有宏任务微任务的划分，使用降级的调用实现就基本都是setTimeout了。

## 📚 参考资料
- [事件循环：微任务和宏任务](https://zh.javascript.info/event-loop)
- https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/#level-1-bossfight