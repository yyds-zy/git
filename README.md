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

#### SSH配置
```
ssh-keygen -t rsa -b 4096 -C "1311257372@qq.com"
cat ~/.ssh/id_rsa.pub
```

#### 首次使用
```
git init 
git config --global user.email ""
git config --global user.name 
git remote add origin http://xxx.git
```
#### 使用场景说明

一、 master为主分支，develop为开发分支。假设我现在在develop分支将项目开发完成，想要将develop分支代码合并到
master分支。
   具体操作：
```
  先将现在develop本地代码提交到远端。

  1>git add .

  2>git commit -m "提交内容"

  3>git push origin develop

  切换到master本地分支并更新master远端仓库。

  1>git checkout master

  2>git pull origin master

  然后将develop分支的代码合并到master,并同步远端仓库。

  1>git merge develop

  2>git status

  3>git push origin master
```

二、 master为主分支，从主分支拉取新分支feature/music,完成音乐播放器模块并合并到master分支。
    具体操作：
```
  首先切换到需要拷贝的分支保证与远程仓库代码一致，拷贝当前分支，提交远程仓库。

  1>git checkout -b feature/XXX

  2>git push origin feature/XXX

  3>同操作一
```

三、 解决冲突

```
git merge 分支 发生错误日志（Automatic merge failed; fix conflicts and then commit the result）

出现了冲突，在本地调试出正确代码版本并且本地测试完全ok后。再次push到远程仓库。
```

四、 依赖远程仓库 submodule

```
git submodule init && git submodule update
```

五、修改本地分支名与远端分支名

```
修改本地分支名  git branch -m 'new_branch_name'   

同步本地和远程，执行1、2

1. git push origin :"old_branch_name" "new_branch_name"     delete remote old branch push new branch
2. git push origin -u new_branch_name     sync local and remote
```

六、 修改分支名
```
git branch -m main master
git fetch origin
git branch -u origin/master master
git remote set-head origin -a
```

七、 暂存区使用

```
# 暂存当前更改，并添加备注信息
git stash save "my changes"
 
# 列出所有暂存的更改
git stash list
 
# 应用最新的暂存更改
git stash apply
 
# 应用最新的暂存更改并从列表中移除
git stash pop
 
# 删除指定的暂存更改
git stash drop stash@{0}
 
# 清空所有暂存的更改
git stash clear

# 查看stash
git stash show -p stash@{2}
```

八、跨团队合作开发-fork
```
一、概述
       此功能的作用是您可以在Github一对开源项目添加您优化代码。 
       Fork允许你创建一个独立的项目副本，Pull Request则允许你将你的修改推送到原始项目中。这种方式促进了开源协作和贡献，使得项目能够从广泛的社区参与中受益。
二、fork 代码到您的Github仓库
        在github上搜索您要修改的项目代码，并fork到您的仓库中。这样Github会创建该项目的一个完全独立的副本，该副本存储在你自己的GitHub账号下。这个分叉副本可以独立进行修改和更改，而不会影响原始项目。
        https://i-blog.csdnimg.cn/blog_migrate/537069e774fa2ca894bf254d280d2fbb.png
        执行完成后您可以在您的仓库中找到这个项目。
        https://i-blog.csdnimg.cn/blog_migrate/c04d71e2f00658602105d3fae26da0af.png
 三、修改代码
        修改代码您可以先使用git clone将代码克隆到你的电脑上，对代码进行修改后再提交到您的Github仓库中。如果您 对git clone、git add、git commit相关指令您还不熟悉，请参考在命令行中使用Git或在IDEA中使用Git。
四、创建Pull requests
        你对分叉项目进行了一些修改后，你可以提交一个"Pull Request"，也就是提出一个请求，要求原始项目的维护者（或者说项目的所有者）合并你的更改到原始项目中。这个请求包含了你所做的修改的详细描述和解释。
维护者可以查看你的更改，讨论其中的细节，最终决定是否接受你的更改并将其合并到原始项目中

        这时您需切换到Pull requests选项卡，点击 New pull requests并填写相关提交日志信息后点击Create pull requests来创建。
        https://i-blog.csdnimg.cn/blog_migrate/d27c2396f251c885fe054bf221ae251f.png
五、拉取Pull requests 合并【注意此处角色切换】
        如果是您是原开发者，此项目被别人fork然后修改了内容，则您可以打开您项目的Pull requests选项卡。打开之后会看到他人修改的代码详细信息，您可以根据情况选择合并（Merge pull requests）

```

