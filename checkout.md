# Checkout

可以 checkout 一个分支，或者一个提交。

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



