# 状态

查看工作树的状态。

## 用法

```
git status
```

## 形态

```
On branch master
nothing to commit, working tree clean
```

On branch master，告诉你当前所在的分支叫 master。nothing to commit，没什么可以提交的东西，working tree clean，因为工作树是干净的。意思就是你的项目还没做什么修改，比如修改了文件，添加了新文件，删除文件等等。

**修改了文件但还没添加到暂存区：**

```
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

在 Changes not staged for commit 下面列出的是还没有放到暂存区上的修改。modified: README.md 告诉你项目的 README.md 文件被修改过了。no changes added to commit，目前还没添加要提交的东西。也就是说暂存区里面现在还没什么东西。

**添加到暂存区的修改：**

```
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    modified:   README.md
```

Changes to be committed 的意思是将要被提交的修改，下面会列出这次提交包含的所有的修改。

