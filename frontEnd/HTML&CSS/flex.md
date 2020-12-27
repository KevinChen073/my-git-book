<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:32:55
 * @LastEditTime: 2020-12-24 00:00:08
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/frontEnd/flex.md
-->
## flex

flex中比较实用的几个布局方式

- 横向布局: flex-dirction
- 垂直居中: justify-content:
- 自动填满，占据所有区域: stretch
- 占据剩余区域: flex 1。flex的三个属性混合：basis\grow\shrink

### 排列相关
在flex-direction定制后，可以通过align-content或者align-items的方式来进行排列对齐
justify-content 和 align-items的差别
align-content的差别：

### 自动换行
- 多个div自动换行：flex-flow
- 多行文字自动换行：webkit-box `display: -webkit-box;-webkit-line-clamp: 8`