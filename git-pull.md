# git pull

git pull 相当于 git fetch 以后，接着再 git merge。就是它把下载与合并这两个动作结合到一块儿了。

```
git pull 远程
```

远程如果是 origin，当前所在分支是 master，那执行 git pull，就相当于：

```
git fetch origin
git merge origin/master
```

## rebase

```
git pull --rebase 远程
```

加了 --rebase 选项，会用 git rebase 代替 git merge。

## 练习



