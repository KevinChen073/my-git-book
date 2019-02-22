


### Gradle

http://ask.android-studio.org/?/question/869

[Android中的Gradle](https://blog.csdn.net/wqc_CSDN/article/details/53572921)

Gradle是一个基于Apache Ant和Apache Maven概念的项目自动化建构工具。它使用一种基于Groovy的特定领域语言(DSL)来声明项目设置，**抛弃了基于XML的各种繁琐配置**。

通常一个项目里面会有四个build.gradle：

- 项目的build.gradle：在这里边指定了使用的代码仓库，声明了使用的Android Gradle插件版本，在这里边主要是可以对整个项目进行配置，这些配置适用于该项目下的所有Module
- 属于Module的build.gradle：在这里边主要是对于指定的Module进行具体的配置。主要分为三大块：apply plugin（声明了Gradle引入的插件），android（描述了该Android Module在构建过程中的配置参数等信息），dependencies（描述了构建过程中所有依赖的库）。我们绝大部分的配置都是在这里完成。
- 本地配置local.properties：这个文件主要是指定使用的SDK和NDK的路径，一般情况不需要改动。
- 设置settings.gradle：这个里边主要是声明了整个项目所引用的Module，每当新建一个Module时就会自动的添加进来。

### [Android的前世今生](https://mp.weixin.qq.com/s?__biz=MzI1MTAyNzM5Ng==&mid=2649948776&idx=1&sn=2ebd08d1e0370402a702c789385aeb2f&chksm=f1fee8c3c68961d50816b99f3443ff07b75959a63ed0c80d72dafe3cc3d0de7d6f61240ea995#rd)

- 2009年4月30日，Android 1.5 Cupcake (纸杯蛋糕）正式发布。

​    主要更新拍摄/播放影片，并支持上传到Youtube；支持立体声蓝牙耳机，同时改善自动配对性能；最新的采用WebKit技术的浏览器，支持复制/贴上和页面中搜索；GPS性能大大提高；提供屏幕虚拟键盘；主屏幕增加音乐播放器和相框widgets；应用程序自动随着手机旋转；短信、Gmail、日历，浏览器的用户接口大幅改进，如Gmail可以批量删除邮件；相机启动速度加快，拍摄图片可以直接上传到Picasa；来电照片显示。

- 2009年9月15日，Android 1.6 Donut (甜甜圈）版本发布。

​    重新设计的Android Market手势；支持CDMA网络；文字转语音系统（Text-to-Speech）；快速搜索框；全新的拍照接口；查看应用程序耗电；支持虚拟私人网络（VPN）；支持更多的屏幕分辨率；支持OpenCore2媒体引擎；新增面向视觉或听觉困难人群的易用性插件。

- 2009年10月26日，Android 2.0/2.0.1/2.1 Eclair (松饼）版本发布。

​    优化硬件速度；"Car Home"程序；支持更多的屏幕分辨率；改良的用户界面；新的浏览器的用户接口和支持HTML5；新的联系人名单；更好的白色/黑色背景比率；改进Google Maps3.1.2；支持Microsoft Exchange；支持内置相机闪光灯；支持数码变焦；改进的虚拟键盘；支持蓝牙2.1；支持动态桌面的设计。

-  2010年5月20日，Android 2.2/2.2.1  Froyo (冻酸奶）版本发布。

​    整体性能大幅度的提升；3G网络共享功能；Flash的支持；App2sd功能；全新的软件商店；更多的Web应用API接口的开发。

- 2010年12月7日，Android 2.3 Gingerbread (姜饼）版本发布。

​    增加了新的垃圾回收和优化处理事件；原生代码可直接存取输入和感应器事件、EGL/OpenGLES、OpenSL ES；新的管理窗口和生命周期的框架；支持VP8和WebM视频格式，提供AAC和AMR宽频编码，提供了新的音频效果器；支持前置摄像头、SIP/VOIP和NFC（近场通讯）；简化界面、速度提升；更快更直观的文字输入；一键文字选择和复制/粘帖；改进的电源管理系统；新的应用管理方式。

- 2011年2月2日，Android 3.0 Honeycomb (蜂巢）版本发布。

​    优化针对平板 ；全新设计的UI增强网页浏览功能 ；in-app purchases功能。

- 2011年5月11日，Android 3.1 Honeycomb (蜂巢)版本发。

​    经过优化的Gmail电子邮箱 ；全面支持Google Maps ；将Android手机系统跟平板系统再次合并从而方便开发者；任务管理器可滚动，支持USB输入设备（键盘、鼠标等） ；支持Google TV.可以支持XBOX 360无线手柄；widget支持的变化，能更加容易的定制屏幕widget插件。

- 2011年7月13日，Android 3.2 Honeycomb (蜂巢）版本发布。

​    支持7英寸设备；引入了应用显示缩放功能。

- 2011年10月19日，Android 4.0 Ice Cream Sandwich (冰激凌三明治)版本发布。

​    全新的UI；全新的Chrome Lite浏览器，有离线阅读，16标签页，隐身浏览模式等；截图功能；更强大的图片编辑功能；自带照片应用堪比Instagram，可以加滤镜、加相框，进行360度全景拍摄，照片还能根据地点来排序；Gmail加入手势、离线搜索功能，UI更强大；新功能People：以联系人照片为核心，界面偏重滑动而非点击，集成了Twitter、Linkedin、Google+等通讯工具。有望支持用户自定义添加第三方服务；新增流量管理工具，可具体查看每个应用产生的流量，限制使用流量，到达设置标准后自动断开网络。

- 2012年6月28 日，Android 4.1 Jelly Bean (果冻豆）版本发布。

​    更快、更流畅、更灵敏；特效动画的帧速提高至60fps，增加了三倍缓冲；增强通知栏；全新搜索；搜索将会带来全新的UI、智能语音搜索和Google Now三项新功能；桌面插件自动调整大小；加强无障碍操作；语言和输入法扩展；新的输入类型和功能；新的连接类型。

- 2012年10月30日，Android 4.2 Jelly Bean (果冻豆）版本发布。

​    Photo Sphere全景拍照功能；键盘手势输入功能；改进锁屏功能，包括锁屏状态下支持桌面挂件和直接打开照相功能等；可扩展通知，允许用户直接打开应用；Gmail邮件可缩放显示；Daydream屏幕保护程序；用户连点三次可放大整个显示频，还可用两根手指进行旋转和缩放显示，以及专为盲人用户设计的语音输出和手势模式导航功能等；支持Miracast无线显示共享功能；Google Now现可允许用户使用Gamail作为新的数据来源，如改进后的航班追踪功能、酒店和餐厅预订功能以及音乐和电影推荐功能等。

- 2013年7月25日，Android 4.3 Jelly Bean (果冻豆）版本发布。


- 2013年9月4日，Android 4.4 KitKat (奇巧）版本发布。

​    更加整合了自家服务，力求防止安卓系统继续碎片化、分散化。

- **2014年10月15日，Android 5.0 Lollipop (棒棒糖）版本发布。**

​    Android 5.0 系统使用一种新的Material Design设计风格。从图片上就能看到一些全新的设计。从图片上看，这套设计图对 Android 系统的桌面图标及部件的透明度进行的稍稍的调整，并且各种桌面小部件也可以重叠摆放。虽然调整桌面部件透明度对 Android 系统来说并不算什么新鲜的功能，但是加入了透明度的改进。界面加入了五彩缤纷的颜色、流畅的动画效果，呈现出一种清新的风格。采用这种设计的目的在于统一 Android 设备的外观和使用体验，不论是手机、平板还是多媒体播放器。

- **2015年5月28日，Android6.0 Marshmallow（棉花糖）版本发布**。

​    新系统的整体设计风格依然保持扁平化的MeterialDesign风格。Android6.0在对软件体验与运行性能上进行了大幅度的优化。据测试，Android6.0可使设备续航时间提升30%。

- 2015年12月8日，Android6.1 Marshmallow（棉花糖）版本发布。

​    是一个小幅度的更新，以性能优化为主，新增了超过200个的emoji表情支持，以及一些Bug的修复。

- **2016年8月22日，Android 7.0 Nougat（牛轧糖）版本发布。**

​    分屏多任务，全新下拉快捷开关页，通知消息快捷回复，通知消息归拢，加入了夜间深色主题模式，流量保护模式，启用了全新的设置样式，对Doze休眠机制做了进一步的优化，将电话拦截功能变成了一个系统级功能，双击菜单键就能自动切换到上一个应用。

- 2017年5月17日，谷歌I/O 2017开发者大会召开，推出了最新版本Android O，目前已有预览版，稍后会正式发布Android 8.0版本。

​    Android 8.0在原先的基础上增加了许多新的亮点，将提供更好的性能及续航表现，尤其是号称App启动速度快了两倍。这次在用户体验方面更是下足了功夫，其中包括更快、更流畅的操作、更快的启动时间、电池续航改进等等。

- 2018年，推出Android 9.0 Pie

  主打人工智能与Android系统结合



### [android系统架构](https://mp.weixin.qq.com/s?__biz=MzI1MTAyNzM5Ng==&mid=2649948782&idx=1&sn=0a8a87d04ced6a10a9b5719074a85f92&chksm=f1fee8c5c68961d3cf23ad6bc5fd13fb0b11e087d9f477767eb98819b02ae31b019086e852cc#rd)

应用程序层 - 应用程序框架层 - 系统运行库层 - Linux内核层

#### 系统运行库层

系统运行库层包含了系统库及Android运行时

Android运行时由两部分组成：Android核心库集和ART。其中核心库集提供了Java语言核心库所能使用的绝大部分功能，而虚拟机则负责运行Android应用程序。(5.0 以前走的是JIT，5.0以后走的是AOT)



#### Dalvik虚拟机和ART模式

[dvm和jvm的差别](http://www.cnblogs.com/scarecrow-blog/p/5105372.html)

Dalvik 虚拟机采用了一种被称为JIT （Just-in-time）的解释器进行动态编译并执行，因此导致Android App运行时比较慢。

- 该虚拟机和Java虚拟机不太一样，一个是执行文件不同.class文件和.dex文件(java类文件在编译过后，会产生至少一个.class文件包含大量陈余信息，dex文件格式会把所有的.class文件内容整合到一个.dex文件中。即减少了整体文件的尺寸和IO操作，也提高了类的查找速度。
- Java VM是以基于栈的虚拟机(Stack-based)，而Dalvik是基于寄存器的虚拟机(Register-based):显然，后者最大的好处在于可以根据硬件实现更大的优化，这更适合移动设备的特点。      



[ART和dalvik的差别](https://qooah.com/2013/12/02/%E3%80%90%E6%8A%80%E8%A1%93%E6%96%87%E7%AB%A0%E3%80%91%E5%AE%8C%E5%85%A8%E8%AA%8D%E7%9F%A5-android-4-4-%E4%B8%AD-art-%E8%88%87-dalvik-%E6%9C%83%E6%9C%89%E5%A4%9A%E5%A4%A7%E5%88%86%E5%88%A5/)

而ART（Android runtime）模式则是在用户安装App时进行预编译（Ahead-of-time，简称AOT）的，将原本在程序运行时的编译动作提前到应用安装时，这样使得程序在运行时可以减少动态 编译的开销，从而提升Android App的运行效率。



#### Android四大组件

Android四大组件分别是：

​    活动（Activity）： 用于表现功能。

​    服务（Service）： 后台运行服务，不提供界面呈现。

​    广播接收器（BroadcastReceiver）：用于接收广播。

​    内容提供者（Content Provider）： 支持在多个应用中存储和读取数据，相当于数据库。

