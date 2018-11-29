# decorator装饰器

### 类装饰器
本质就是一个高阶函数
```javascript
@decorator
class A {}

// 等同于

class A {}
A = decorator(A) || A;
```

但是和高阶函数不同的是：
> 修饰器对类的行为的改变，是代码编译时发生的，而不是在运行时。这意味着，修饰器能在编译阶段运行代码。也就是说，修饰器本质就是编译时执行的函数。

### 类方法（属性）装饰器
还是高阶函数，只是入参不同
```javascript
function log(target, name, descriptor) {}
```
target为原型
name为函数名
descriptor.value为方法。可用于劫持打log，打点等方法

### 一般用法
- 静态属性修改(通过修改对象属性)
- 动态属性修改（通过prototype)
- 修改类的属性方法

### 常见
- redux的connect
- core-decorators.js是一个第三方模块，提供了几个常见的修饰器，通过它可以更好地理解修饰器。