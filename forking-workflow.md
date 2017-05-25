# Forking 工作流

## 练习

Hulk 觉得

```
git clone https://github.com/hulk8080/ninghao-git.git hulk-git
```

```
→ git remote -v
origin    https://github.com/hulk8080/ninghao-git.git (fetch)
origin    https://github.com/hulk8080/ninghao-git.git (push)
```

```
git remote add upstream https://github.com/ninghao/ninghao-git.git
```

```
→ git remote -v
origin    https://github.com/hulk8080/ninghao-git.git (fetch)
origin    https://github.com/hulk8080/ninghao-git.git (push)
upstream    https://github.com/ninghao/ninghao-git.git (fetch)
upstream    https://github.com/ninghao/ninghao-git.git (push)
```

```
git config --local user.name 'hulk8080'
git config --local user.email 'hulk@ninghao.net'
```

```
git checkout -b feature-branch
git pull upstream master
git push origin feature-branch
```

维护人

```
git fetch https://github.com/hulk8080/ninghao-git.git feature-branch
git checkout master
git merge FETCH_HEAD
git push origin master
```

所有人

```
git pull upstream master
```



