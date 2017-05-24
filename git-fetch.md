# git fetch

git fetch 可以把远程仓库里的东西下载到本地。

```
git fetch 远程 分支
```

## 练习

**1**，在本地的 ninghao-git 目录下面做点修改，提交以后，再推送给远程仓库。比如修改一下 README.md，内容如下：

```
# Git :)
一本关于 Git 的书。

## 流程

## 分支

---
by ninghao.net
```

做一次提交：

```
git commit -am '在说明文档里添加“分支”章节'
```

推送给远程：

```
git push
```

返回：

```
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 384 bytes | 0 bytes/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:ninghao/ninghao-git.git
   e0efae3..f4b6009  master -> master
```

打开远程仓库页面，观察项目的 commits ，你会发现刚刚推送上来的一个提交。

**2**，现在换个身份，我假装自己是小雪，在介绍  git clone 的时候，我已经把 ninghao-git 这个项目克隆下来了，放在一个叫 xiaoxue-git 的目录里。进入到这个目录，查看历史：

```
cd ~/desktop/xiaoxue-git
git log --oneline
```

最近几条提交：

```
e0efae3 为仓库文档添加一段描述
2d49d40 添加仓库文档的大标题
35e1941 添加介绍 Git 仓库的文档
```

**3**，练习 git fetch。假装我还是小雪，我要用 git fetch，下载刚才推送到远程的新的提交，执行：

```
git fetch origin master
```

返回：

```
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/ninghao/ninghao-git
 * branch            master     -> FETCH_HEAD
   e0efae3..f4b6009  master     -> origin/master
```

git fetch 把远程 master 分支上的新东西下载到了本地，默认这些新东西会在本地的远程分支上，在这里这个分支应该是 origin/master。查看本地上的远程分支，执行：

```
git branch -r
```

返回：

```
origin/HEAD -> origin/master
origin/master
```

查看远程分支 origin/master 的历史，执行：

```
→ git log origin/master --oneline
```

返回：

```
f4b6009 在说明文档里添加“分支”章节
e0efae3 为仓库文档添加一段描述
2d49d40 添加仓库文档的大标题
```

你会发现，在本地上的远程分支 origin/master 上，有新做的提交 _**在说明文档里添加“分支”章节**_，说明刚才我们已经成功的用 git fetch，把远程上的新东西下载到本地了。

**4**，合并远程分支。现在要把本地远程分支上的东西合并到本地 master 分支上。

```
git checkout master
git merge origin/master
```

查看 master 的历史，现在会是：

```
→ git log --oneline

f4b6009 在说明文档里添加“分支”章节
e0efae3 为仓库文档添加一段描述
2d49d40 添加仓库文档的大标题
```

本地 master 分支上，已经包含了从远程那下载下来的提交了。

