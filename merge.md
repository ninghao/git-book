# 合并

把两个分支合并到一块儿。你为了新想法，新功能，或者修复项目的 bug 创建了一些分支，最终你还是希望把这些分支合并到主分支上。Git 有几种合并算法，Fast-Forward 合并，3-Way 合并。

```
git merge 分支
```

## 练习

**1**，Fast-Forward 合并练习。介绍分支的时候我们创建了一个新分支叫 smiley-face，在这个分支上做了一次提交。这期间在主分支（master）上没发生什么变化，也就是没在主分支上修改项目，没做提交，也没有合并其它的分支。这样我们在把 smiley-face 分支合并到 master 分支上的时候，就会是一个 Fast-Forward 合并。

先把当前分支切换到 master，执行：

```
git checkout master
```

观察项目里的文档，现在文档里面还没有我们在 smiley-face 上做的修改，也就是在文档里添加的笑脸符号。然后去合并 smiley-face 分支，执行：

```
git merge smiley-face
```

返回：

```
Updating 2b9a260..546fc18
Fast-forward
 README.md    | 2 +-
 resources.md | 2 +-
 2 files changed, 2 insertions(+), 2 deletions(-)
```

显示了一个 Fast-forward，表示这次合并是一次 Fast-forward 合并。查看项目的 master 分支上的历史：

```
→ git log --oneline -n 3

546fc18 在文档中添加笑脸符号
2b9a260 去掉文档中的笑脸符号
fd3acec 在说明文档里添加流程章节
```

最近的 “在文档中添加笑脸符号” 这个提交，是我们在 smiley-face 分支上做的，在 master 分支上合并了这个 smiley-face 分支以后，这些提交你都可以在 master 上找到。

**2**，合并时使用 --no-ff，表示不使用 Fast-forward 合并，这样可以在历史里记录一下合并动作。先重置一下 master ，抹掉合并以后加进来的提交：“在文档中添加笑脸符号”，执行：

```
git reset HEAD~1 --hard
```

现在 master 的历史会是：

```
→ git log --oneline -n 3

2b9a260 去掉文档中的笑脸符号
fd3acec 在说明文档里添加流程章节
e648ade 在相关资源里添加一个资源列表项目
```

重新再去合并一下 smiley-face，这次合并的时候用一个 --no-ff 选项，执行：

```
git merge smiley-face --no-ff
```

返回：

```
Merge made by the 'recursive' strategy.
 README.md    | 2 +-
 resources.md | 2 +-
 2 files changed, 2 insertions(+), 2 deletions(-)
```

提示合并用了 recursive 策略。用了 --no-ff 选项以后，在合并的时候会做一次新的提交。再这样查看一下历史：

```
git log --oneline --graph
```

显示：

```
→ git log --oneline --graph
*   981ec29 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
|/  
* 2b9a260 去掉文档中的笑脸符号
* fd3acec 在说明文档里添加流程章节
```

加上 `--graph` 选项查看历史，会为你标记出使用 --no-ff 选项以后的合并。

```
→ git log --oneline -n 3
e35e925 Merge branch 'smiley-face'
546fc18 在文档中添加笑脸符号
2b9a260 去掉文档中的笑脸符号
```

**3**，练习 3-Way 合并。再去重置一下 master 分支，执行：

```
git reset HEAD~1 --hard
```

现在的 master 的历史会是：

```
→ git log --oneline --graph

* 2b9a260 去掉文档中的笑脸符号
* fd3acec 在说明文档里添加流程章节
* e648ade 在相关资源里添加一个资源列表项目
```

然后我们在 master 分支做点提交，假设现在有个 bug 或者功能急着要，你可以基于 master 去创建一个新的分支，在上面去修复 bug 或添加新功能，完成以后把它们合并到 master 上。

这里我们直接修改一下 master 分支下的东西。修改 README.md，像这样：

```
# Git
一本关于 Git 的书。

## 流程

---
by ninghao.net
```

然后做一次提交：

```
git commit -am '在说明文档底部添加内容作者'
```

现在，再去合并一下 smiley-face 分支：

```
git merge smiley-face
```

在合并的时候虽然没用 --no-ff，但是也会提交我们要做一次合并提交，因为 Git 现在不能做 Fast-forward 提交。

```
Auto-merging README.md
Merge made by the 'recursive' strategy.
 README.md    | 2 +-
 resources.md | 2 +-
 2 files changed, 2 insertions(+), 2 deletions(-)
```

查看一下合并之后的历史：

```
→ git log --oneline --graph

*   8d26980 Merge branch 'smiley-face'
|\  
| * 546fc18 在文档中添加笑脸符号
* | 907acdc 在说明文档底部添加内容作者
|/  
* 2b9a260 去掉文档中的笑脸符号
```

再像这样查看一下历史：

```
→ git log --oneline

8d26980 Merge branch 'smiley-face'
907acdc 在说明文档底部添加内容作者
546fc18 在文档中添加笑脸符号
2b9a260 去掉文档中的笑脸符号
```



