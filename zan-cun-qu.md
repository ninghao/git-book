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

**1**，继续修改项目。打开项目下的 README.md 添加一行文字：git，保存文件，查看状态：

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



