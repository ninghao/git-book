# git remote

现在我们准备好去为项目创建一个远程仓库。

## 用法

列出远程仓库：

```
git remote
```

详细显示：

```
git remote -v
```

添加远程仓库：

```
git remote add 名字 地址
```

删除远程仓库：

```
git remote rm 名字
```

重命名远程仓库：

```
git remote rename 旧名字 新名字
```

## 创建远程仓库

在一个远程仓库服务商那里为项目创建一个远程仓库。比如用你在 Github 申请的帐号，去创建一个仓库。[https://github.com/new](https://github.com/new)

输入 Repository name，仓库的名字，还有 Description，仓库的描述。选择仓库的类型，可以是 Public，公开，任何人都能看到你的仓库里的内容。也可以是 Private，私有，只有你，还有你允许的人才能看到仓库里的内容。

在创建仓库时我为仓库起的名字是 ninghao-git，所以这个仓库的地址应该是：

```
https://github.com/ninghao/ninghao-git.git
```

或者 SSH 形式的仓库地址：

```
git@github.com:ninghao/ninghao-git.git
```

一般远程仓库都有两种地址，一种是 https，一种是 ssh。这两种地址使用的验证方法不一样，https 用的是用户名 + 密码的方式验证你的身份。ssh 会使用 ssh-key 作为验证身份的方法。

