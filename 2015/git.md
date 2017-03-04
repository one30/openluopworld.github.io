---
layout: default
---

# 日常工作中用到的git命令
2015.08.20

[Git]是一个开源的分布式版本控制工具，最初是由[Linus]在[Linux]的开发过程中为了更好的管理代码而开发。[GitHub]是基于Git实现的一个可视化的管理工具，这篇文章主要记录我在平常工作中用到的一些Git命令。都是非常基础的操作，可以作为一个入门的参考。

![Git](https://git-scm.com/images/logo@2x.png)

### 基本操作

设本地目录：/home/zh/gitcodes

远端项目地址：https://github.com/zh/Test

#### 1. 用户信息配置
```sh
// 进入到本地目录
cd /home/zh/gitcodes
// 配置用户信息，分别配置用户名和邮箱信息
git config --global user.name "name" //例如：git config --global user.name "amani"
git config --global user.email "email" // 例如：git config --global user.email "amani@good.com"
```

#### 2. 开发
```sh
// 克隆远程项目
git clone https://git.oschina.net/luop/Test
```

```sh
// 项目clone后保存在gitcodes目录下，要想进行相应的操作我们需要先进入到该目录。
cd Test // Test即是远端项目的名字
```

```sh
// 接下来便可以对文件做增加，删除，修改操作；完成后可以先使用diff命令查看具体修改的内容
// 该命令将查看本次所有的改动，可以方便工程师了解所做的改动是否和自己预期的一致，这可以防止错误修改
// 使用diff命令后可以通过q退出
git diff
```

```sh
// 提交本次修改
// 提交修改到本地的仓库
git add --all
// 查看本次修改的文件（包括修改的(modified)，增加的(added)，删除的(deleted)3种类别），但只给出文件名，没有具体修改细节；
git status
// 提交本次改动给远端仓库，双引号中的内容是对本次提交做的简单说明，好的说明可以方便自己和组内其他成员了解所做的改动，这和代码注释的道理一样
git commit -m "commit information"
// 正式提交，远端仓库的内容将会进行修改；需要输入用户名和密码
git push
```

#### 3. 查看版本历史
```sh
// 可以查看当前分支的日志，即使用git commit向仓库提交新版本时附加的版本更新信息
git log 
// 可以查看当前分支的每一个版本大致变动情况，平常不怎么用到
git log --stat --summary
// versionId是版本号（可以使用完整的，较常见的是只使用前面部分字符），可以查看对应提交版本对项目更改的详细内容
git show versionId
// git diff也能实现同样的功能
git diff versionId
```
![gitdiff](http://1.lpxq.sinaapp.com/images/201508/20150820pic1.png)

#### 4. 分支管理

对于系统S的模块A和B，比如需要对模块A进行修改（比如增加功能，或尝试另一种方法优化目前可以运行的代码），而同时模块B仍继续开发。可以在T节点（某个时刻）创建一个新的分支单独对A进行修改，当修改成功后再将A合并到主分支。一般情况下，如果模块划分的足够好，自T节点之后主分支不会对A进行修改，因此当合并时不会有冲突。如果有冲突手动解决就好了。

* 在当前分之的基础上创建新分支，分支名为branchName，新分支创建后内容会从当前分支复制一份。

```sh
git branch branchName
```

* 在切换分支之前先查看当前所处分支

```sh
git branch // 查看本地分支
git branch -r // 查看远程分支
```

* 切换到本地分支branchName，切换之前先保证本分支的修改都已提交

```sh
git checkout branchName
```

* 新创建的分支在第一次提交时，远程是没有的；因次需要通过origin来提交。在新分支提交成功后即可直接通过git push完成

```sh
git push origin branchName
```

* [删除远程分支]：当一个分支temp的功能完成后，通过merge命令将其合并到相应的分支上。这样temp分支即可删除。

```sh
git push origin --delete temp // temp为分支名
```

* fork的项目更新源项目的提交

```sh
// git remote add origin_name git@github.com:username/projectname
// git fetch origin_name
// the two commands are equal to the following command
git fetch original_project_url
```

这有关于[Git flow分支管理]的文章，有兴趣可以看看。

#### 5. git pull

多数情况下，一个项目由很多开发人工共同完成，即使是同一个功能模块也会有多人参与。因此在正式对代码修改之前，应先通过git　pull从远端拉取最新的代码合并到本地，再在此基础上进行开发。这是一个非常好的习惯，可以避免修改后才发现远端分支已做过修改。一种更直接的方法是每天工作完成后清除本地仓库，第二天开始工作时重新使用git clone命令从远端下载，再进行开发。

```sh
git pull // 从远端分支取出更新版本，然后合并到本地分支中
```

上面只给出了一些非常基础的Git命令，实际工作中需要不断根据应用需求学习...


  [Git]:<https://git-scm.com/>
  [Linus]:<https://en.wikipedia.org/wiki/Linus_Torvalds>
  [Linux]:<https://en.wikipedia.org/wiki/Linux>
  [GitHub]:<https://github.com/>
  [删除远程分支]:<http://zengrong.net/post/1746.htm>
  [Git flow分支管理]:<http://my.oschina.net/boomya/blog/691480>
