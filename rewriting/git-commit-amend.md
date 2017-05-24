# git commit --amend

你想修改一下刚刚做的这次提交，比如修改提前的信息，或者把新的修改放到刚做的这次提交里。可以使用 git commit 命令，加上一个 --amend 选项：

```
git commit --amend
```

注意执行了上面的命令会生成一次新的提交，替换掉刚刚做的那次提交。如果你上次做的提交已经分享给其他人了，那你不应该使用上面这条命令。

## 练习

**1**，修改一下 README.md 的文件，内容如下：

```
# Git :)
一本关于 Git 的书。

## 流程
```

做一次提交：

```
git commit -am '流程'
```

查看历史：

```
→ git log --oneline -n 3
687260e 流程
e648ade 在相关资源里添加一个资源列表项目
14b8235 在说明文档里添加一段描述
```

哦，最近做的这次提交的信息我要改一下。执行：

```
git commit --amend
```

这会打开编辑器，让你重新输入一条提交信息。完成以后，再查看历史：

```
→ git log --oneline -n 3
fd3acec 在说明文档里添加流程章节
e648ade 在相关资源里添加一个资源列表项目
14b8235 在说明文档里添加一段描述
```

注意最近做的这次提交是一个全新的提交，观察一下提交的 ID，你会发现跟之前是不一样的。

**2**，修改 README.md，resources.md，去掉大标题最后的笑脸符号。然后再提交一下修改，执行：

```
git add README.md
git commit -m '去掉文档中的笑脸符号'
```

做完这次提交以后，我发现还有一处修改应该也加到这次提交里。所以，执行一下：

```
git add resources.md
git commit --amend --no-edit
```

这次用了一个 `--no-edit`，表示不想编辑提交信息，直接用以前的就行。查看一下历史，再检查一下最近做的那次提交。

```
→ git log --oneline -n 3
2b9a260 去掉文档中的笑脸符号
fd3acec 在说明文档里添加流程章节
e648ade 在相关资源里添加一个资源列表项目

→ git show 2b9a260
commit 2b9a2606ffb71b9f711f84cd85f7d0eea4045e97
Author: wanghao8080 <117663444@qq.com>
Date:   Wed May 24 08:37:36 2017 +0800

   去掉文档中的笑脸符号

diff --git a/README.md b/README.md
index fdcae3b..8d1a6e8 100644
--- a/README.md
+++ b/README.md
@@ -1,4 +1,4 @@
-# Git :)
+# Git
一本关于 Git 的书。

## 流程
diff --git a/resources.md b/resources.md
index 995248e..61456d0 100644
--- a/resources.md
+++ b/resources.md
@@ -1,2 +1,2 @@
-# 相关资源 :)
+# 相关资源
* 宁皓网《Git》课程包
```



