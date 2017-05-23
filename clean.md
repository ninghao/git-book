# Clean

Clean，清理。把未跟踪的文件清理掉。

## 练习

**1**，在项目下面新建一个文件，名字是 demo.md。

```
touch demo.md
```

然后查看状态，会返回：

```
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    demo.md

nothing added to commit but untracked files present (use "git add" to track)
```

提示有个未跟踪的文件：demo.md，现在我要把它清理掉，执行：

```
git clean -f
```

返回：

```
Removing demo.md
```

查看状态：

```
On branch master
nothing to commit, working tree clean
```

demo.md 被 Git 干掉了。

