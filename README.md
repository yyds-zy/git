# Git

#### 使用教程

1.  删除本地分支  git branch -d 本地分支名
2.  删除远端分支  git push --delete origin 远端分支名
3.  创建本地分支  git branch 本地分支名
4.  创建远端分支/提交本地分支到远端  git push origin 本地分支名
5.  切换本地分支  git checkout 本地分支名
6.  切换远端分支  git checkout origin 远端分支名
7.  关联远程仓库  git remote add origin 远程仓库地址
8.  初始化创建仓库  git init
9.  拷贝分支、上传远端  git checkout -b feature/voip 、git push origin feature/voip
10. 提交代码  git commit -m "提交内容"
11. 基于现有分支拉出一条新分支 git checkout -b feature/xxx   git push origin feature/xxx
12. 基于远程仓库分支拉出一条本地不存在的分支 git checkout -b feature/xxx origin/feature/xxx

#### 首次使用
git init 
git config --global user.email ""
git config --global user.name 
git remote add origin http://xxx.git

#### 使用场景说明

一、 master为主分支，develop为开发分支。假设我现在在develop分支将项目开发完成，想要将develop分支代码合并到
master分支。

   具体操作：

...先将现在develop本地代码提交到远端。

  1>git add .

  2>git commit -m "提交内容"

  3>git push origin develop

...切换到master本地分支并更新master远端仓库。

  1>git checkout master

  2>git pull origin master

...然后将develop分支的代码合并到master,并同步远端仓库。

  1>git merge develop

  2>git status

  3>git push origin master

二、 master为主分支，从主分支拉取新分支feature/music,完成音乐播放器模块并合并到master分支。

    具体操作：

... 首先切换到需要拷贝的分支保证与远程仓库代码一致，拷贝当前分支，提交远程仓库。

  1>git checkout -b feature/XXX

  2>git push origin feature/XXX

  3>同操作一

三、 解决冲突

... git merge 分支 发生错误日志（Automatic merge failed; fix conflicts and then commit the result）

出现了冲突，请不要慌，在本地调试出正确代码版本并且本地测试完全ok后。再次push到远程仓库。

四、 依赖远程仓库 submodule

git submodule init && git submodule update

五、修改本地分支名与远端分支名

修改本地分支名  git branch -m 'new_branch_name'   

同步本地和远程，执行1、2

1. git push origin :"old_branch_name" "new_branch_name"     delete remote old branch push new branch
2. git push origin -u new_branch_name     sync local and remote

四、 修改分支名
git branch -m main master
git fetch origin
git branch -u origin/master master
git remote set-head origin -a

