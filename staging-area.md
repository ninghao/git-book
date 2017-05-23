# 暂存区

Staging Area，暂存区 / 中间区。把对项目做的修改，先放到暂存区，然后再做提交。

## 用法

把对某个文件的所有修改添加到暂存区：

```
git add <文件>
```

把在某个目录下做的所有修改添加到暂存区：

```
git add <目录>
```

把做的所有修改还有新的文件添加到暂存区（不包含删除文件）：

```
git add .
```

把所有东西放到暂存区（修改，新文件，删除文件）：

```
git add -A
```

把做的所有修改还有删除添加到暂存区：

```
git add -u
```

## 练习

**1**，继续修改项目。打开项目下的 README.md 添加一行文字：\# git，保存文件，查看状态：

```
git status
```

返回：

```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

**2**，为项目添加一个新文件。新建一个项目文件：

```
touch resources.md
```

再次查看状态：

```
git status
```

返回：

```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    resources.md

no changes added to commit (use "git add" and/or "git commit -a")
```

现在工作目录里面有两个文件可以提交一下，一个是修改之后的 README.md，还有一个新文件是 resources.md。提交之前你得把修改添加到暂存区，可以添加所有修改，也可以只选择其中的一小部分。

**3**，把修改添加到暂存区。执行：

```
git add README.md
```

查看状态会返回：

```
→ git status
On branch master
Changes to be committed:
 (use "git reset HEAD <file>..." to unstage)

 modified:   README.md

Untracked files:
 (use "git add <file>..." to include in what will be committed)

 resources.md
```

Changes to be committed 下面列出的就是将要提交的东西，上面显示了 modified: README.md。如果现在做提交，这个提交里面会包含对 README.md 文件做的所有修改。

**4**，做一次提交，执行：

```
git commit -m '设置说明文档的标题'
```

查看状态，你会发现：

```
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    resources.md

nothing added to commit but untracked files present (use "git add" to track)
```

显示工作区上还有个未跟踪的文件 resources.md，之前在暂存区的 README.md 已经不在了，因为我们做了提交。再把 resources.md 放到暂存区准备提交：

```
git add .
```

这次我在 add 后面用了一个点，它表示所有的修改还有未跟踪的文件。查看状态会返回：

```
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   resources.md
```

再去提交一下：

```
git commit -m '添加相关资源文档'
```

查看提交历史，执行：

```
git log --oneline
```

返回：

```
23f3c2b 添加相关资源文档
a454700 设置说明文档的标题
39975b3 初始化
```



