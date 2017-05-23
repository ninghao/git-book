# Checkout

可以 Checkout 一个分支，或者一个提交。

## 练习

**1**，先做两次提交。修改项目下的 README.md 还有 resources.md，在标题的结尾添加一个笑脸符号。

README.md

```
# git :)
```

resources.md

```
# 相关资源 :)
```

再去提交一下：

```
git commit -am '让标题微笑'
```

然后再单独修改一下 README.md，把标题中的 git 修改成 Git：

```
# Git :)
```

再提交一下：

```
git commit -am '让 README.md 标题的首字母大写'
```

查看一下历史：

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

**2**，Checkout 一个提交。查看提交历史会显示每个提交的 ID，比如我这里做的 “添加相关资源文档” 这个提交的 ID 是 23f3c2b。

```
23f3c2b 添加相关资源文档
```

执行：

```
git checkout 23f3c2b
```

返回：

```
Note: checking out '23f3c2b'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 23f3c2b... 添加相关资源文档
```

观察 resources.md 这个文档的变化。你会发现这个文档的标题不见了，因为对这个文档的标题的修改保存在了 “设置相关资源文档标题” 这个提交里。我们当前的位置是在做这个提交之前的一个提交。查看一下提交日志，你会发现：

```
→ git log --oneline
23f3c2b 添加相关资源文档
a454700 设置说明文档的标题
39975b3 初始化
```

**3**，Checkout 一个分支。关于分支我们会在后面介绍到。默认我们的项目有个 master 分支，Checkout 到这个分支，执行：

```
git checkout master
```

返回：

```
→ git checkout master
Previous HEAD position was 23f3c2b... 添加相关资源文档
Switched to branch 'master'
```

观察项目文件的变化，再查看一下项目提交的历史。

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



