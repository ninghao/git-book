# 提交

Commit（提交）就是把修改保存到仓库里。

## 用法

```
git commit
```

## 选项

* -a（--all），把所有修改与删除自动添加到暂存区然后提交。不包含未跟踪文件。
* -m（--message），设置提交信息。

## 练习

**1**，打开 resources.md ，添加一行文字：

```
# 相关资源
```

保存文件，再去修改一下：

```
git commit -am '设置相关资源文档标题'
```

这次用了 `-a` 选项，它会自动把所有的修改放到暂存区，然后提交。

