# hoodinn git workflow


## 分布式仓库:
![](http://gitlab.hd.com/qinx/git-workflow/raw/master/git-workflow/repository.png)

每个人本地的git都是一个仓库，每次在`git push/pull`的时候跟服务器进行同步。

## 工作流
![](http://gitlab.hd.com/qinx/git-workflow/raw/master/git-workflow/git-workflow.png)

1. 默认情况下，初始化的时候只有一个`master`分支。 
2. `git checkout -b develop` 创建一个新develop分支。 
3. 发布的时候在`develop`的基础上，创建一个release分支: `git checkout -b release-1.0.0`

其他情况：
1. feature分支： 功能性分支
2. bugfix分支：修复bug用

## 合并
![](http://gitlab.hd.com/qinx/git-workflow/raw/master/git-workflow/git-merge.png)

