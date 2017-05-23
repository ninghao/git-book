# 仓库

Repository，仓库，简称 Repo。为项目添加一个 Git 仓库以后，你就可以用 Git 为项目做版本控制了。

```
git init
```

上面的命令可以为项目初始化一个仓库，这个动作只需要执行一次，它会在项目下面创建一个 .git 目录，Git 会把它需要的东西存储在这个 .git 目录里面，它其实就是项目的仓库。

## 练习

**1**，创建一个项目。打开你的命令行界面，执行：

```
cd ~/desktop
mkdir ninghao-git
cd ninghao-git
touch README.md
```

在桌面上创建了一个项目 ninghao-git，在项目里添加了一个空白的 README.md 文件。

**2**，初始化一个仓库。执行：

```
git init
```

返回：

```
Initialized empty Git repository in /Users/wanghao/Desktop/ninghao-git/.git/
```

初始化了一个空白的 Git 仓库，位置是：

```
/Users/wanghao/Desktop/ninghao-git/.git/
```

查看一下项目下面的东西：

```
ls -la
```

你会看到一个 .git 目录，再观察一下这个目录下面的东西：

```
ls -l .git
```

返回：

```
-rw-r--r--   1 wanghao  staff   23  5 23 11:22 HEAD
-rw-r--r--   1 wanghao  staff  137  5 23 11:22 config
-rw-r--r--   1 wanghao  staff   73  5 23 11:22 description
drwxr-xr-x  12 wanghao  staff  408  5 23 11:22 hooks
drwxr-xr-x   3 wanghao  staff  102  5 23 11:22 info
drwxr-xr-x   4 wanghao  staff  136  5 23 11:22 objects
drwxr-xr-x   4 wanghao  staff  136  5 23 11:22 refs
```

或者如果你在系统上安装了 `tree`，可以查看目录的树形结构：

```
→ tree .git

.git
├── HEAD
├── config
├── description
├── hooks
│   ├── applypatch-msg.sample
│   ├── commit-msg.sample
│   ├── post-update.sample
│   ├── pre-applypatch.sample
│   ├── pre-commit.sample
│   ├── pre-push.sample
│   ├── pre-rebase.sample
│   ├── pre-receive.sample
│   ├── prepare-commit-msg.sample
│   └── update.sample
├── info
│   └── exclude
├── objects
│   ├── info
│   └── pack
└── refs
   ├── heads
   └── tags

8 directories, 14 files
```

你不用太操心 .git 目录里的东西，Git 会为你管理。

