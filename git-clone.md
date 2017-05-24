# git clone

git clone ，能把远程仓库完整地复制一份，放到本地的某个目录的下面。

## 练习

**1**，克隆一个远程仓库。我们之前创建了一个公开的远程仓库，也就是任何人都可以把这个仓库内容 clone 到他们自己的电脑上。这里我们假装自己是另外一个人，打开电脑上的命令行工具，进入到桌面上，然后再去 clone 一份自己创建的远程仓库。

```
cd ~/desktop
git clone https://github.com/ninghao/ninghao-git.git xiaoxue-git
```

上面的命令会把 ninghao 的 ninghao-git 这个远程仓库克隆到本地电脑上的 xiaoxue-git 这个目录。

执行 git clone 时返回的信息：

```
Cloning into 'xiaoxue-git'...
remote: Counting objects: 52, done.
remote: Compressing objects: 100% (31/31), done.
remote: Total 52 (delta 5), reused 52 (delta 5), pack-reused 0
Unpacking objects: 100% (52/52), done.
```





