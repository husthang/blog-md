---
title: Git笔记
date: 2016-11-16 17:36:59
tags: [Git]
description: Git基础,GitHub使用
categories: 奇技淫巧
---
## GitHub团队合作
1. [Team Collaboration With GitHub](https://code.tutsplus.com/articles/team-collaboration-with-github--net-29876)
    [中文翻译在这](http://xiaocong.github.io/blog/2013/03/20/team-collaboration-with-github/)
2. [如何同步 Github fork 出来的分支](http://jinlong.github.io/2015/10/12/syncing-a-fork/)    

## Git基础

### add,commit
- `git log`,`git log --pretty=oneline`只显示一行
- `git add <file>` `git commit -m "..."`
- commit id: 这是一个由 40 个十六进制字符（0-9 和 a-f）组成字符串，基于 Git 中文件的内容或目录结构计算出来,SHA-1散列
- commit: 每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为commit。提交一个commit快照,就相当于保存了一次版本
- 所有的版本控制系统，只能跟踪纯文本文件的改动，比如TXT文件，网页，所有的程序代码等等. 二进制文件(如图片,视频等)可以管理,但不能跟踪改动.

### 版本回退
- 版本回退:在Git中，用`HEAD`表示当前版本，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，往上100个版本可以写成`HEAD~100`。 `git reset --hard HEAD^`退回到上一个版本(即这时文件的内容与结构和上次的commit时的一样了). `git reflog`查看命令历史，以便确定要回到未来的哪个版本
- 总结
	+ HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset commit_id`,不指定参数,则默认soft。
	+ 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。`git log --pretty=oneline`,显示简洁版日志
	+ 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

### 工作区和暂存区
- ![示意图](/images/工作区暂存区示意图.jpeg)
- `git add`命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行`git commit`就可以一次性把暂存区的所有修改提交到分支

### 撤销修改
- `git diff HEAD -- file`查看工作区和版本库里面最新版本的区别
- 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。**此命令含义,从index暂存区,检出此文件更新工作区**
- 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD file`(**reset直接跟文件,默认mixed**,这个命令的全部是: `git reset --mixed HEAD file`含义是将file从HEAD版本复制到暂存区),这个命令让暂存区恢复,然后只需要丢弃工作区的修改即可,这就回到了场景1，从暂存区检出此文件. **此场景方法二**: 直接一步到位`git checkout HEAD -- file`同时撤销本地和暂存区修改.

### 重置解密
- [reset与checkout](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E9%87%8D%E7%BD%AE%E6%8F%AD%E5%AF%86#_git_reset)
- reset
	+ ![`git reset --soft HEAD~`](/images/reset-soft.png)
	+ ![`git reset --mixed HEAD~`](/images/reset-mixed.png)
	+ ![`git reset --hard HEAD~`](/images/reset-hard.png)
- `checkout`:`git checkout [tree-ish] -- file`
	+ 如果不指定commit,则默认从index暂存区的内容覆盖本地修改
	+ 如果指定了commit,从commit版本复制出来更新index索引和工作区的修改.[参考](http://cnblog.me/2015/08/15/git-checkout/)

### 标签管理
- tag就是一个让人容易记住的有意义的名字，它跟某个commit绑在一起
- 命令`git tag <name>`用于新建一个标签，默认为HEAD，也可以指定一个commit id；
- [参考](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376951758572072ce1dc172b4178b910d31bc7521ee4000)

### 忽略文件
- .gitignore文件 [.gitignore模板](https://github.com/github/gitignore)
- [参考](https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E8%AE%B0%E5%BD%95%E6%AF%8F%E6%AC%A1%E6%9B%B4%E6%96%B0%E5%88%B0%E4%BB%93%E5%BA%93#忽略文件)

### git分支
- 命令
	+ 查看分支：git branch
	+ 创建分支：git branch <name>
	+ 切换分支：git checkout <name>
	+ 创建+切换分支：git checkout -b <name>
	+ 合并某分支到当前分支：git merge <name>
	+ 删除分支：git branch -d <name>
- HEAD
	+ 在Git中，HEAD是一个指针，指向版本库中当前所在的本地分支(将 HEAD 想象为当前分支的别名)
- 远程分支
	+ 以`(remote)/(branch)`形式命名,远程分支与远程仓库通信时会自动移动.
	+ `git fetch origin` 拉取远程仓库,并移动远程分支,**注意**`git pull`命令比较"魔法",不推荐使用,应显示的使用`git fetch`与`git merge`.
	+ `git push (remote) (branch)`把本地branch分支,推送到远程remote.详细:`git push origin serverfix:serverfix`，含义“推送本地的 serverfix 分支，将其作为远程仓库的 serverfix分支”
- 参考
	+ [GitBook分支](https://git-scm.com/book/zh/v2/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%AE%80%E4%BB%8B)

## FAQ
1. git GUI推荐:[SourceTree](https://www.sourcetreeapp.com/)
