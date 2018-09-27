charles的使用方法

#### 什么是charles
一般而言，charles用于抓取请求，并且结合代理服务器的形式，一般可用于无线调试抓取请求。
使用场景：
- 抓取本地本机的网路请求
- 代理服务器，抓取其他终端（PC、APP、其他手机浏览器）的网络请求

#### charles使用简介
网上很多，参考即可：http://blog.devtang.com/2015/11/14/charles-introduction/

#### 注意事项

1. 现在网站基本都用https，对这类型网站，必须让手机安装代理服务器（就是你的电脑）的ssl证书，通常而言是在手机上访问`charlesproxy.com/getssl`获取。（当然，如果charles升级了，看charles的help就可以了）

2. 对IOS系统，证书安装以后，还需要设置信任证书：“设置”>“通用”>“关于本机”>“证书信任设置”
https://support.apple.com/zh-cn/HT204477

3. 一般而言，APP内的请求都是有APP加密的。如淘宝、Alibaba.com、微信等都有。这类型的话，就需要APP的测试包，把APP加密功能先暂时移除掉。