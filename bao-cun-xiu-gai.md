# 保存修改

对项目做了一点修改，把修改保存到项目的开发历史里。这样以后你就可以查看项目在某个时间点都做了哪些修改，修改里都动了哪个文件，具体修改的内容是什么，是谁做的修改。你还可以恢复之前对项目做的修改。

## 查看状态

查看当前都修改了项目的哪些东西。

```
git status
```

## 添加修改

添加要保存的修改的地方。

```
git add 文件/目录
```

## 提交修改

把添加的修改提交到 Git 仓库。

```
git commit
```

## 查看历史

看一下项目都做了哪些提交。

```
git log
```

## 练习

**1**，先查看一下之前我们创建的项目当前状态。执行：

```
git status
```

返回：

```
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README.md

nothing added to commit but untracked files present (use "git add" to track)
```

提示 Untracked files ，未跟踪的文件：README.md。这个文件是创建项目的时候添加的一个文件，想用 Git 跟踪这个文件的变化，你得告诉 Git 一声。

**2**，把修改添加到暂存区，准备提交。执行：

```
git add README.md
```

再查看一下现在工作区的状态，会返回：

```
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   README.md
```

注意这次的显示跟之前查看状态的时候会有变化。Changes to be committed ，将要提交的修改下面有个 new file：README.md，意思是这次要提交的东西里面，包含了一些新文件  README.md 。

**3**，提交修改。执行：

```
git commit -m '初始化'
```

返回：

```
[master (root-commit) 39975b3] 初始化
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

提交修改用的是 git commit ，加上 -m 选项可以为提交的修改添加一条备注信息。

**4**，查看历史，执行：

```
git log
```

返回：

```
commit 39975b3b097c383a2a48d3d69719dce5e83222b1
Author: wanghao8080 <117663444@qq.com>
Date:   Tue May 23 11:53:29 2017 +0800

    初始化
```



