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

最后，重启studio，让gradle的配置生效

### 从零开始Android开发

- Android Studio的下载与安装
- 相关环境：Java、SDK、Jar包下载
- 模拟器选择：Android Virtual Device Manager，搞一台虚拟设备（或者你也可以用真实手机）


## Gradle相关
http://www.flysnow.org/2015/03/30/manage-your-android-project-with-gradle.html

### Gradle中添加依赖
- repositories，代表你的依赖的获取地方，可以是线上。也可以是本地
- dependencies，具体的依赖包名
- classpath: buildscript itself needs something to run, use classpath
- compile 是从repository（默认是jCenter())里下载一个依赖包进行编译并打包
- provided 是提供给那些只编译不打包场景的命令。就是，我在编译的时候对某一个jar文件有依赖，但是最终打包apk文件时，我不想把这个jar文件放进去，可以用这个命令 as3.0以后为：compileOnly。
- compile 是从本地的libs目录下寻找picasso-2.4.0.jar这个文件进行编译并打包。类似的命令有`compile fileTree(dir: 'libs', include: '*.jar')`——将
- compile project 是将另一个module（等同eclipse中的library)进行编译并打包
- as3.0以后，compile命令换成了implementation或者api。api全等于compile，而implementation则是编译后内部形成闭包，不对外暴露，见：https://blog.csdn.net/lyh1299259684/article/details/78567828

http://blog.jobbole.com/72992/\

### Gradle的Plugin配置
`apply plugin: 'com.android.application'`

### setting.gradle
settings.gradle用于配置project，标明其下有几个module，比如这里包含一个:app module
`include ':app'`

### Gradle等版本的关系
Android Stuido版本
Gradle-4.6-all
com.android.tools.build:gradle:3.2.0
compileSdkVersion=26
buildToolsVersion="26.0.3" 

### NDK
更新NDK版本。但如果某个项目只支持某个NDK版本，那么可以在SDK设置中使得项目编译使用NDK16

### [armeabi不支持](https://juejin.im/post/5afe28446fb9a07aa0483d0a)
armeabi-v7a兼容.
ABIs [armeabi] are not supported for platform.
最新的NDK r17版本，已经去掉了armeabi、mips、mips64的ABI支持。
[三种ABI库是什么](https://blog.csdn.net/dxpqxb/article/details/7721156)

### 目录结构
res 代码中R可以直接访问
assets 资源文件，需要用getAssets()方法

### UI组件
[重要的ui组件——Behavior](http://www.cnblogs.com/android-blogs/p/5867398.html)
[CoordinatorLayout布局的使用方式](https://www.jianshu.com/p/97206f5973c5)

### minifest设置
android:name设置方式

### 接入WEEX
WEEX的运行机制，引擎源代码

### 常见问题
- Program type already present: 需要允许多版本。`multiDexEnabled true`。同时问题导致的原因是因为：引用了多个版本
https://stackoverflow.com/questions/51942596/error-program-type-already-present-com-thoughtbot-expandablerecyclerview-build
https://stackoverflow.com/questions/49676155/what-does-program-type-already-present-mean/49767860

- Gradle could not resolve project: 需要配置Project的compile(implementation)方式。原因是由于module之间的buildTypes不一致导致的
https://stackoverflow.com/questions/44830256/gradle-could-not-resolve-project-linkedin-sdk/45522379
http://www.jcodecraeer.com/a/anzhuokaifa/Android_Studio/2017/1026/8646.html
