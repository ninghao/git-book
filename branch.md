# 分支

开发项目的时候，有了新的想法，但你又不太确定想法是否可行，或者你打算为项目开发一项新功能。都可以去创建一个新的分支，在上面去实践你的想法，如果可行，或者在新分支上完成了你想要的功能，你可以再把在这个分支上对项目做的修改合并到主分支或开发分支上。完成以后，可以保留这些分支，也可以把它们删除掉。

## 列出分支

```
git branch
```

## 创建分支

```
git branch 新分支
```

## 删除分支

```
git branch -d 分支
```

或使用更狠的删除：

```
git branch -D 分支
```

## 重命名分支

```
git branch -m 分支的新名字
```

## 练习

**1**，查看项目的分支列表，执行：

```
git branch
```

返回：

```
* master
```

当前只有一个分支叫 master，分支名前面的 `*` 号表示这是当前你所在的分支。

**2**，创建一个新的分支，执行：

```
git branch smiley-face
```

上面我创建了一个叫 smiley-face 的分支，因为在这个分支上我们要在项目文档里添加些笑脸符号。

再查看一下分支列表，现在会显示：

```
* master
  smiley-face
```

多了一个分支叫 smiley-face，但当前所在的分支仍然是 master。

**3**，切换分支，执行：

```
git checkout smiley-face
```

上面命令会把当前分支切换到 smiley-face ，可以查看分支列表确定一下：

```
→ git branch

  master
* smiley-face
```

这次 \* 号跑到 smiley-face 那儿去了，表示当前的分支是 smiley-face。

**4**，修改项目，修改 README.md 与 resources.md，在文档上添加两个笑脸符号。

README.md

```
# Git :)
一本关于 Git 的书。

## 流程
```

resouces.md

```
# 相关资源 :)
* 宁皓网《Git》课程包
```

提交一下：

```
git commit -am '在文档中添加笑脸符号'
```

查看历史：

```
→ git log --oneline -n 3
546fc18 在文档中添加笑脸符号
2b9a260 去掉文档中的笑脸符号
fd3acec 在说明文档里添加流程章节
```

因为我们当前所在的分支是 smiley-face，在上面做的提交都属于这个分支。

**5**，把分支切换到 master 分支，观察项目的变化。

```
git checkout master
```

查看提交历史，你不会找到刚才我们在 smiley-face 上做的提交。观察项目文档里的内容，你也不会看到添加的笑脸符号。

