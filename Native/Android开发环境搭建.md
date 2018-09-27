# Android开发相关知识树

- 开发环境IDE：Android Studio、Jar包、Android SDK
- 语言Java or Kotlin
- 体系：纯Android、Flutter、Weex
- 包管理和构建工具：Gradle
- Android生命周期
- 构建打包机制
- kexue 上网

### 关于初次运行Gradle超级慢
运用Android Studio 进行首次构建项目时候，会出现Gradle构建画面，但由于网络问题，会持续好长时间。因为通常gradle项目都在gradle\wrapper\gradle-wrapper.properties中配置在线gradle。
```
#Tue Sep 20 11:58:39 CST 2016
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-2.14.1-all.zip
```
这个其实可以把离线包下载下来，然后配置Gradle从本地安装。
https://blog.csdn.net/jamesshaoya/article/details/73412981

### 从零开始Android开发

- Android Studio的下载与安装
- 相关环境：Java、SDK、Jar包下载
- 模拟器选择：Android Virtual Device Manager，搞一台虚拟设备（或者你也可以用真实手机）
