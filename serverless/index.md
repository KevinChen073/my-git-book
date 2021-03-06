<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-12-15 14:35:42
 * @LastEditTime: 2020-12-15 14:50:16
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/serverless/index.md
-->
# 服务器部署
> Create by 远宏 2020.12.14  
> Update by 远宏 2020.12.14 

## 什么是容器
可以独立承载应用，并且相互文件系统、环境配置隔离的进程。因为只做到了部分隔离（操作系统是没有隔离的），所以虚拟器启动时间分钟级、容器达到秒级；内存占用也能够达到MB级别，一台机器可以承载远超虚拟机数量的容器。同时提供了镜像概念，让回滚和部署变得简单。但是缺点也是隔离不完全，同时非界面的学习成本也会比较大。
虚拟机面向虚拟资源隔离，容器面向应用隔离。

## K8s、Docker、Serverless之间的关系
关于服务器部署，机器和容器区分开来，以往一台机器就是一个容器，并且承载多个应用。而目前则是一台机器可以提供多个容器对应多个应用。Docker则是容器化的一种最佳实践，基于容器化就可以做到以往不好进行的快速扩容（统一容器快速部署）、镜像回滚（给容器注入不同的镜像版本）。而k8s则是多个容器的管理系统。由于容器和K8s的产生，让开发人员可以不关系服务器部署的相关事情，只关注内部的部署的能力，像Saas、Faas等也就应运而生了。

容器化技术的演进和Serverless思想：
- 服务端机器更合理地运营，一台机器能够多支持应用部署 -> 
- 虚拟机、Docker -> 
- Docker的内存占用、启动时间都有明显优势（因为不用单独隔离操作系统）-> 
- 镜像概念（环境配置 + 应用程序）-> 
- 快速部署、扩容、回滚 -> 
- 多机器多容器的管理 -> 
- k8s -> 
- 运维的成本降低，可以更加核心关注在服务上 -> 
- Serverless的思想

### 一句话描述
一句话：Docker是容器化技术的最佳实践，K8s是用于管理容器关系的。减少了服务部署的成本后，正正迎合了Serverless的需求，让开发者更多关注在服务上，甚至让前端也可以加入在容器中部署服务或者函数，Saas、Faas

### 一些参考文章
[Docker与Kubernetes的前世今生](https://www.infoq.cn/article/zs05fled2orqvutkb7mj)、[什么是K8s](https://www.redhat.com/zh/topics/containers/what-is-kubernetes)