---
title: Revert
---

# 撤消

Revert 命令可以撤消之前做过的某个提交。

## 练习

**1**，先查看一下项目的提交历史：

```
→ git log --oneline
fb11f83 让 README.md 标题的首字母大写
0fd9dac 让标题微笑
7086650 添加 .gitignore
b5773ad 设置相关资源文档标题
23f3c2b 添加相关资源文档
a454700 设置说明文档的标题
39975b3 初始化
```

“添加 .gitignore” 这个提交的 ID 是 7086650。

**2**，撤消提交。要撤消 “添加 .gitignore”，执行：

```
git revert 7086650
```

会打开编辑器，让你输入一条提交信息。默认会像这样：

```
Revert "添加 .gitignore"

This reverts commit 70866505bdc3f302c5676467579c4bf3e212e6b4.
```

退出编辑器，然后查看项目下的文件，你会发现 .gitignore 这个文件已经不在了，因为我们 Revert 了 “添加 .gitignore” 这个提交，这个提交里包含的修改就是添加了一个叫 .gitignore 的文件，Revert 这个提交就是删除掉 .gitignore 文件。

现在的提交历史像这样：

```
→ git log --oneline
795b30d Revert "添加 .gitignore"
fb11f83 让 README.md 标题的首字母大写
0fd9dac 让标题微笑
7086650 添加 .gitignore
b5773ad 设置相关资源文档标题
23f3c2b 添加相关资源文档
a454700 设置说明文档的标题
39975b3 初始化
```

**3**，再试一次撤消提交。这次撤消 “让标题微笑”  这个提交，这个提交的 ID 是 0fd9dac，先查看一下这个提交：

```
git show 0fd9dac
```

返回：

```
commit 0fd9daccbd06d7c73602ba60deb75fd38ea5e923
Author: wanghao8080 <117663444@qq.com>
Date:   Tue May 23 16:31:59 2017 +0800

    让标题微笑

diff --git a/README.md b/README.md
index 8d36a8e..d705f07 100644
--- a/README.md
+++ b/README.md
@@ -1 +1 @@
-# git
+# git :)
diff --git a/resources.md b/resources.md
index a756bd0..c7d04ae 100644
--- a/resources.md
+++ b/resources.md
@@ -1 +1 @@
-# 相关资源
+# 相关资源 :)
```

这个提交包含了两处修改，修改了 README.md 的标题，添加了笑脸符号，修改了 resources.md ，也在标题的最后添加了笑脸符号。

执行撤消：

```
git revert 0fd9dac
```

提示：

```
error: could not revert 0fd9dac... 让标题微笑
hint: after resolving the conflicts, mark the corrected paths
hint: with 'git add <paths>' or 'git rm <paths>'
hint: and commit the result with 'git commit'
```

这次 Revert 的时候出错了，提示 conflicts ，发生冲突了。查看状态，返回：

```
On branch master
You are currently reverting commit 0fd9dac.
  (fix conflicts and run "git revert --continue")
  (use "git revert --abort" to cancel the revert operation)

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   resources.md

Unmerged paths:
  (use "git reset HEAD <file>..." to unstage)
  (use "git add <file>..." to mark resolution)

	both modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	access.log
```

提示：

```
You are currently reverting commit 0fd9dac
```

正在撤消提交 0fd9dac，但是有冲突，有冲突的文件是 README.md，打开这个文件看一下，里面的内容像这样：

```
<<<<<<< HEAD
# Git :)
=======
# git
>>>>>>> parent of 0fd9dac... 让标题微笑
```

把发生冲突的地方修改成你想要的样子，应该像这样：

```
# Git
```

保存文件，然后执行：

```
git add README.md
```

再提交一下：

```
git commit -m 'Revert "让标题微笑"'
```

这样这次撤消就完成了。查看历史：

```
→ git log --oneline
33c97bc Revert "让标题微笑"
3dc2c3f Revert "添加 .gitignore"
fb11f83 让 README.md 标题的首字母大写
0fd9dac 让标题微笑
7086650 添加 .gitignore
b5773ad 设置相关资源文档标题
23f3c2b 添加相关资源文档
a454700 设置说明文档的标题
39975b3 初始化
```



