<!--
 * @Author: 星啸(陈远宏)
 * @Date: 2020-11-24 09:47:41
 * @LastEditTime: 2020-12-15 14:50:06
 * @LastEditors: 星啸(陈远宏)
 * @Description: 
 * @FilePath: /my-git-book/git/[操作]关于git的双开.md
-->
 # 双开github，gitlab
> Create by 远宏 2020.11.24  
> Update by 远宏 2020.12.14 

 [github,gitlab双开](https://juejin.cn/entry/6844903501248593933)
 
 操作中才记起来，github和gitlab的双开。既需要配置本地git软件，也需要配置git仓库的username

 ## 基本排错
 如果commit中发现提交人不是github账户，那十有八九是拉取的仓库中，git config配置成了另一个账号。
1. 在本地git仓库中输入`git config -l`查询username和email
2. git `git config --local user.name 'xxx'`配置用户名
3. 配置Email `git config --local user.email 'xxx'`