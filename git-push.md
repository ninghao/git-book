# git push

git push 可以把在本地对项目做的提交上传到远程仓库。

> 《硅谷》第四季第一集开场 5 分钟左右。Gilfoyle 问 Richard：“Did you push you code？”。这里说的应该就是使用 git push 命令，把代码上传到远程仓库。

## 用法

```
git push 远程 分支
```

## 练习

**1**，我们已经为项目添加了一个远程仓库，现在可以把项目 push 到远程仓库了，执行：

```
git push -u origin master
```

意思就是把本地的 master 推送到 origin 这个远程上。加上了 -u 选项以后，下面你再 push 的时候，可以直接执行：

```
git push
```

第一次执行 push 以后返回的东西：

```
Counting objects: 52, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (36/36), done.
Writing objects: 100% (52/52), 5.40 KiB | 0 bytes/s, done.
Total 52 (delta 5), reused 0 (delta 0)
remote: Resolving deltas: 100% (5/5), done.
To github.com:ninghao/ninghao-git.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
```

完成以后，刷新远程仓库页面，你会看到 push 上来的项目。

