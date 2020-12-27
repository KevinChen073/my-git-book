#generator用法
参考：https://imququ.com/post/generator-function-in-es6.html

## 具体原理
### 外部使用
生成器函数 -> 生成器 -> 调用生成器的next -> 返回数据

```
function *foo(){} // 生成器函数
let bar = foo(); // 生成器
let k = bar.next(); //滴啊用生成器的next
k; // 数据
```

### 内部编写
生成器（函数的实例），每次被调用next的时候，就执行到yield，并且return yield的右值
```
function* foo(list) {
    for(var i = 0; i < list.length; i++) {
        yield list[i];
    }
    return 'done';
}

let bar = foo([1,2,3]);
let k1 = bar.next(); // k1.value = 1
let k2 = bar.next(); // k2.value = 2
let k3 = bar.next(); // k3.value = 3
// 不能直接用forEach来循环，因为forEach不是生成器，没办法返回yield
```


### 结合框架的异步编程同步化
例如Q.js，可以允许我们传入生成器函数，并且自动生成生成器。在每一个yield Promise调用resolve的时候，自动调用其next方法，做到多个异步调用能够同步进行。（当然，是个假同步了，在Q语块外面，我们还是需要考虑同步异步的问题）

```
var all = Q.async(function* () {
    var src = yield getData(); // 一个异步promise
    var img = yield getImg(src); // 又一个异步promise
    showImg(img);
});

all();
```
### babel支持