# Reset

Reset，重置。

## 练习

1，先查看历史：

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



