# for的N种用法
参考：https://juejin.im/entry/5a1654e951882554b8373622

## forEach
函数回调forEach，注意闭包问题。

## for循环
不说了

## for in
ES5就有的for循环，主要是查数组和对象的索引，例如
```javascript
let k = ['a','b','c'];
for (let index in k) {
    console.log(index);
    // index为0，1，2，3
}

let k = {a: 2,b: 3,c: 4};
for (let index in k) {
    console.log(index);
    // index为a,b,c
}
```
但由于数组也是个对象，会把一些原型方法也查出来，因此我们一般结合hasOwnProperty来用

## for of
为了解决ES5的问题，有一个for of。这个for of是用于查值，例如

```javascript
let k = ['a','b','c'];
for (let index of k) {
    console.log(index);
    // index为a,b,c
}

// 对象会报错，不能走遍历
let k = {a: 2,b: 3,c: 4};
for (let index of k) {
    console.log(index);
    // index为a,b,c
}
```
同时，这个也可以遍历Set、Map等集

## so……
数组用for of，for，forEach
对象用for in
