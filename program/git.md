关于git能力的记录

首先是……推荐sourceTree这款mac上的git仓库管理软件。可视化的操作：git文件的拉取、推送、管理、合并。同时可以查看git仓库的权限配置等
## 基本git操作

### 推送拉取
- checkout
- pull
- add
- commit
- push

### 查询git仓库
- remote -v：查询远端仓库地址
- config -l:查询此git仓库的相关配置

修改当前的git仓库配置：
```
git config --add user.name xxx
git config --add user.email xxx@yy.com
```

### git状态
- (git status)[https://www.yiibai.com/git/git_status.html] 管理当前项目git状态