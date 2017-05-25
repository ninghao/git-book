# 冲突

小雪再 pull 的时候遇到了冲突。

```
→ git pull --rebase

remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/ninghao/ninghao-git
  70161b2..25e582e  master     -> origin/master
First, rewinding head to replay your work on top of it...
Applying: 为说明文档章节添加描述文字
Using index info to reconstruct a base tree...
M    README.md
Falling back to patching base and 3-way merge...
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
error: Failed to merge in the changes.
Patch failed at 0001 为说明文档章节添加描述文字
The copy of the patch that failed is found in: /Users/wanghao/desktop/xiaoxue-git/.git/rebase-apply/patch

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort".
```

于是她查看状态，看看到底发生了什么事情：

```
→ git status
rebase in progress; onto 25e582e
You are currently rebasing branch 'master' on '25e582e'.
 (fix conflicts and then run "git rebase --continue")
 (use "git rebase --skip" to skip this patch)
 (use "git rebase --abort" to check out the original branch)

Unmerged paths:
 (use "git reset HEAD <file>..." to unstage)
 (use "git add <file>..." to mark resolution)

 both modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

引起冲突的是 README.md ，打开这个文件，里面的内容如下：

```
# Git :)
一本关于 Git 的书。

## 流程
<<<<<<< HEAD
了解使用 Git 的基本流程。 
=======
介绍 Git 的使用流程。
>>>>>>> 为说明文档章节添加描述文字

## 分支
创建与管理项目的分支。

## 远程
为项目添加远程仓库。

## 协作
用 Git 协作开发项目。

---
by ninghao.net
```

冲突的地方是：

```
## 流程
<<<<<<< HEAD
了解使用 Git 的基本流程。 
=======
介绍 Git 的使用流程。
>>>>>>> 为说明文档章节添加描述文字
```

因为小雪 pull 下来的远程提交里面，也修改了流程章节下面的描述。小雪要解决这个冲突，她觉得自己写的比较写，于是她这样修改了发生冲突的地方：

```
# Git :)
一本关于 Git 的书。

## 流程
介绍 Git 的使用流程。

## 分支
创建与管理项目的分支。

## 远程
为项目添加远程仓库。

## 协作
用 Git 协作开发项目。

---
by ninghao.net
```

再添加一下：

```
git add README.md
```

继续 rebase ：

```
→ git rebase --continue
Applying: 为说明文档章节添加描述文字
```

完美地解决了冲突，push：

```
→ git push

Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 476 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/ninghao/ninghao-git.git
  25e582e..20c43d5  master -> master
```

![](/assets/github-repo-multi-commits.png)

