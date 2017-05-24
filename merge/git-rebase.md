# git rebase

不解释，直接练：）

## 练习

**1**，我们的项目是一本 git-book，现在我们要去添加一个新文档，介绍一下 Git 的 “仓库”。创建一个分支，执行：

```
git checkout -b repo-doc
```

在 git checkout 命令里用了 -b 选项，这样如果要查看的分支不存在，就会给我们创建一个。查看分支，显示当前是在 repo-doc 这个分支上。

```
  master
* repo-doc
```

在项目下面新建一个 Markdown 文件：

```
touch repository.md
```

做一次提交：

```
git add .
git commit -m '添加介绍 Git 仓库的文档'
```

打开 repository.md，在文档里添加一个标题：

```
# 仓库
```

再做一次提交：

```
git commit -am '添加仓库文档的大标题'
```

**2**，现在假设项目有个突发状况，可能是一个要立即修复的 bug，或者添加一个功能。不管是什么吧，反正是要立即完成的事儿。先切换回 master 分支：

```
git checkout master
```

为修复的 bug，或添加的功能创建一个分支：

```
git checkout -b 'add-bottom-text'
```

打开项目下的 resources.md，把文档修改成这样：

```
# 相关资源 :)
* 宁皓网《Git》课程包

---
by ninghao.net
```

执行一次提交：

```
git commit -am '为 resouces.md 添加底部文字'
```

把 add-bottom-text 合并到 master：

```
git checkout master
git merge add-bottom-text
```

再把 add-bottom-text 删除掉：

```
git branch -d add-bottom-text
```

现在 master 分支上会有一个来自 add-bottom-text 的提交：

```
→ git log --oneline --graph
* 40670e5 为 resouces.md 添加底部文字
```



