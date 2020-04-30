---
title: "Git Learning"
date: 2020-03-24T17:04:16Z
draft: true
---

之前学习了git差不多又忘记了，所以今天再复习一下，然后做一下记录，我之前都是在[廖雪峰](https://www.liaoxuefeng.com/wiki/896043488029600/897889638509536)的网站上学习的。而且发现git的命令已经改了，所以必须自己记录一下了。

里面介绍的非常详细，我这里只记录一下自己的学习。

## add与commit

这是两个基本动作，在不出错的情况下，会这两个就够了。
```
工作区
└── 版本库
    ├── 暂存区
    └── 分支
```
我的理解是这样的，add把修改添加到暂存区，commit把修改提交到分支。


一次成功是最好的结果，可是人生啊就是在不到的错误中前进的。因此修改重来是常用的事。

## 修改与撤销

当没有提交到分支时：

`git status`查看暂存区状态，

`git diff  --<file>`，查看文件的修改情况

`git diff`显示出了工作区与暂存区不同的所有修改。

`git restore <file>...`来恢复，把暂存区的文件拿出来覆盖了工作区，慎用啊，不小心把自己写好的东西弄丢了就不好了。 

添加是对暂存区进行覆盖，恢复是对工作区进行覆盖。

`git rm <file>`删除暂存区的文件。

## 版本回退

版本库记录了每一次提交，也记录了每一次的命令操作。

`git log`查看提交日志，

`git reflog`查看对版本库的每次命令操作。

有了这两个命令，就可以在不同版本里来回穿梭了。

`git reset --hard HEAD`，来回退版本

在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。

这种方式只能不断的往前回退，不能去新的版本。

另外一种方式是使用版本号，就是那段非常长的数，每一个版本都有它唯一的编号。
```
$ git reset --hard 1094a
```
可以以此在不同版本间穿梭，那个号不用全写完，足够git找到就行。

回退版本就把工作区的文件覆盖了，所以回退操作前也要谨慎。



## git设置忽略排除和重新添加已经忽略的文件(夹)

重新添加已经被忽略过的文件（夹）：

git rm -r --cached . 

清空暂存区，再重新添加。


