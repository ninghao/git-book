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



