# 蝴蝶GIT工作流

## 1.分布式仓库:
![](http://gitlab.hd.com/qinx/git-workflow/raw/master/git-workflow/repository.png)

每个人本地的git都是一个仓库，每次在`git push/pull`的时候跟服务器进行同步。

## 2.工作流
![](http://gitlab.hd.com/qinx/git-workflow/raw/master/git-workflow/git-workflow.png)

1. 默认情况下，初始化的时候只有一个`master`分支。 
2. `git checkout -b develop` 创建一个新develop分支。所有的开发都在这个分支上操作
3. 发布的时候在`develop`的基础上，创建一个release分支: `git checkout -b release-1.0.0`，并在这个分支上打包和发布版本

其他分支（一般情况只存在于本地git库）：
1. feature分支： 功能性分支，可以在`develop`或`release`上面checkout出来，根据实际情况决定。
2. bugfix分支：修复bug用，一般情况是在release分支上checkout出来，用于临时修复release上的bug

## 3.合并
![](http://gitlab.hd.com/qinx/git-workflow/raw/master/git-workflow/git-merge.png)

合同的时候带上参数`--no-ff`， 这样可以保留提交的记录.

## 4.现场演示

1. 初始化一个项目
mkdir gitdemo
cd gitdemo


```bash
#初始化相关

git init
git remote add githd git@gitlab.hd.com:qinx/git-demo.git # 推荐使用ssh方式操作git

# 查看git remote
git remote -v
```

```bash
# 完成一次提交, 初始化
touch README.md
git add README.md
git commit -am 'added README'
git push -u githd master
```
 

```bash
# 创建develop 分支
git branch -vv  #查看当前分支
git checkout -b develop
vim test.js
git add test.js
git commit -am 'added test.js'
git push -u githd develop
# or git push
```
 

```bash
# 发布版本1.0 
git checkout -b release-1.0.0
./package_updated.sh
```
 

```bash
# 修复线上发布的版本bug

git checkout release-1.0.0
git checkout -b bug-wrongname  # 这个分支一般仅仅存在于本地.
# 开始修复bug

# git merge --no-ff release-1.0.0

#返回release-1.0.0
git checkout release-1.0.0
git merge --no-ff bug-wrongname

#如果有冲突，则人工修复
#发布
./package_updated.sh

``````
