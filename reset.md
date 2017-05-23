# Reset

Reset，重置。

## 练习

**1**，重置。先查看一下历史：

```
→ git log --oneline
33c97bc Revert "让标题微笑"
3dc2c3f Revert "添加 .gitignore"
fb11f83 让 README.md 标题的首字母大写
0fd9dac 让标题微笑
7086650 添加 .gitignore
b5773ad 设置相关资源文档标题
23f3c2b 添加相关资源文档
a454700 设置说明文档的标题
39975b3 初始化
```

现在我想把项目的状态重置到刚做完 “让 README.md 标题的首字母大写” （fb11f83） 这个提交。也就是重围以后，这个提交之后的所有的提交都会被抹掉。

重置，执行：

```
git reset --hard fb11f83
```

返回：

```
HEAD is now at fb11f83 让 README.md 标题的首字母大写
```

HEAD 表示头部指针，现在它的位置是在 “fb11f83 让 README.md 标题的首字母大写” 这个提交上。查看历史：

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

注意 “让 README.md 标题的首字母大写” 这个提交以后的提交都已经不见了。

**2**，重置暂存区。先打开 README.md ，在标题下面添加一行文字：

```
# Git :)
一本关于 Git 的书。
```

再打开 resources.md，也在标题下添加一行文字：

```
# 相关资源 :)
* 宁皓网《Git》课程包
```

查看状态：

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
	modified:   resources.md

no changes added to commit (use "git add" and/or "git commit -a")
```

把修改添加到暂存区：

```
git add .
```

再次查看状态：

```
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   README.md
	modified:   resources.md

```

两处修改都在暂存区了。如果想重置暂存区上的东西，执行：

```
git reset
```

返回：

```
Unstaged changes after reset:
M	README.md
M	resources.md
```

提示把之前添加到暂存区的两处修改从暂存区里拿出来了。

再试一下：

```
git add .
```

然后：

```
git status
```

这次把对 resources.md 文件的修改从暂存区里拿出来。执行：

```
git reset resources.md
```

提交一下：

```
git commit -m '在说明文档里添加一段描述'
```

再执行：

```
git add .
```

然后再次提交：

```
git commit -m '在相关资源里添加一个资源列表项目'
```

历史现在变成了：

```
→ git log --oneline
e648ade 在相关资源里添加一个资源列表项目
14b8235 在说明文档里添加一段描述
fb11f83 让 README.md 标题的首字母大写
0fd9dac 让标题微笑
7086650 添加 .gitignore
b5773ad 设置相关资源文档标题
23f3c2b 添加相关资源文档
a454700 设置说明文档的标题
39975b3 初始化
```



