关于跨端能力相关

### Native


### React Native
#### 手势
- RN的手势玩法：https://github.com/jabez128/jabez128.github.io/issues/1
- RN的Touch事件：https://blog.csdn.net/qq_30053399/article/details/77776049
RN的手势除了基本的Toucable组件以外，要给其他组件添加手势，都是通过一系列的事件，包括是否（捕获，点击、移动、释放）的事件，而且里面考虑到了事件间的优先级等（使用捕获来解决）

但是由于比较贴近Native思维，个人感觉纯Web开发者难以理解

### WEEX
- RAX手势实现：https://github.com/alibaba/rax/

Rax是基于WEEX，再封装成React语法的上层库，因此手势语法参考了RN的一套

- WEEX手势

基本就是Touchstart\move\end三套件