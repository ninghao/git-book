## .gitignore

在项目里，不想用 Git 跟踪的文件可以列在 .gitignore 文件里。

## 练习

**1**，在项目根目录下，创建一个文件：

```
touch access.log
```

查看状态，你会发现：

```
Untracked files:
    access.log
```

Git 认为 access.log 这个文件是还未跟踪的文件。如果你想在项目里忽略掉这种 .log 结尾的文件，也就是不想把它们放到项目的仓库里，可以创建一个 .gitignore 文件，在里面列出你想忽略掉的文件。

**2**，在项目根目录下，创建一个文件：

```
touch .gitignore
```

文件里的内容如下：

```
*.log
```

意思是忽略掉 .log 结尾的文件。再次查看状态，在未跟踪的文件列表里，之前显示的 access.log 已经不见了。因为我们在 .gitignore 里明确地告诉 Git，\*.log 这种文件我们不想跟踪。

**3**，提交：

```
git add .
git commit -m '添加 .gitignore'
```



