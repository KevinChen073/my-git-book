### node自动化保持状态
一般用于保持状态的方式是创建一个隐藏的文件，最好是这个文件不要随着git一起提交即可。主要练习文件IO以及写JSON的注意事项

### 项目抽离
一般而言，config、helper、constant、common这类型都是编写项目的好习惯
- config.json：通用的项目配置
- constant：一些常量，尽量不要在项目中使用Magic Number
- helper：对项目用的方法，例如拉取、build、copy、deploy、打log等

### helper的抽离
一般而言，helpers里面都是对项目有帮助的通用性能力的抽离。
- 例如获取路径、获取变量
- 运行编译构建
- 部署相应文件
- 打log

### setup的抽离
用于对helper、constant等文件进行第一次初始化写入。常常包括copy，创建目录。脚手架形式的问答等