## 工作流程

工作区 -> 暂存区 -> 仓库（本地仓库+远程仓库）

## Git 配置

```bash
git config --global user.name 'ifer'
git config --global user.email 'ifer@qq.com'
```

```bash
# 查看所有的全局配置项
git config --global --list
# 查看指定的全局配置项
git config --global user.name
git config --global user.email
```

## Git 基本操作

- 初始化仓库，`git init`

- 查看文件的状态，`git status / git status -s`

- 添加到暂存区，`git add . / git add index.html`

- 提交到仓库，`git commit -m '新增了 index.html 文件'`

- `git remote add origin https://github.com/ifer-itcast/test57.git`

- `git push -u origin master`，第一次提交到远端

- `git push`，后续提交直接 git push

- `git checkout . / git checkout -- index.html`，慎用，不可逆，撤销工作区的修改

- `git reset HEAD . / git reset HEAD index.html`，撤销暂存区的提交

- `git commit -a -m '跳过暂存区直接提交到仓库'`，要保证此文件曾经 add 过

- `git rm -rf index.html`，删除本地和仓库的 index.html 文件，了解即可

- `git log`，查看 commit 历史，`git reflog`

- `git reset --hard CommitId（提交 ID）`，掌握！


- `.gitignore 里面可以写需要被忽略的文件`

```bash
# * 就代表任意字符，能匹配例如 a.a，bb.a，xxx.a 的文件，都能忽略
*.a

# 忽略 node_modules 这个文件夹
node_modules/
```


## 几个小命令

- `ls`，列出当前目录的文件列表

- `clear`，`ctrl + l`，清屏

- `touch index.html`，创建文件

- `mkdir test`，创建文件夹

- `cat index.html`，在终端查看 index.html 的内容


## SSH

```bash
echo "# test233" >> README.md
git init
git add README.md
git commit -m "first commit"
# git branch -M main
git remote add origin git@github.com:ifer-itcast/test233.git
# git push -u origin main
git push -u origin master
```

- 删除已经关联的远端地址：`git remote remove origin`

## Git 基本流程

1. [下载 Git](https://git-scm.com/download/win)

2. 注册 GitHub 账号

配置本机全局的用户名（username）和密码（password）

```bash
git config --global user.name 'ifer'
git config --global user.email 'ifer@qq.com'
```

3. 配置 SSH

```bash
ssh-keygen -t rsa -b 4096 -C "ifer@qq.com"
```

去 C:\Users\用户名文件夹\.ssh 目录打开 id_rsa.pub 文件，把文件的内容粘到 GitHub 的对应的配置里面`点击头像 -> Settings -> SSH and GPG Keys -> New SSH key`

检测是否配置成功，能看到 success 就成功了

```bash
ssh -T git@github.com
```

4. New repository

- 远端通过 `New repository` 新建仓库

- 本地新建一个空的文件夹，执行下面代码

```bash
echo "# 说明" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:ifer-itcast/test233.git
git push -u origin master
```

5. 以后的所有文件的修改，只需要

```bash
git add .
git commit -m '提交信息'
git push
```

6. 如果说本地不在了

```bash
git clone git@github.com:ifer-itcast/test233.git
```

## 分支

```bash
# git branch // 查看
git branch 注册功能 // 创建
git checkout 注册功能 // 切换

# git checkout -b 注册功能 // 创建并切换分支

然后就可以在 “注册功能” 分支上进行开发，开发往后进行 git add .，git commit -m '提交信息'

git checkout master // 切换到 master 分支
git merge 注册功能 // 合并注册功能的代码
```

- 创建分支的时候，创建的分支的代码和当前所处的分支的代码一样

- 如果想把 a 分支的代码合并到 b 分支上面，要先保证处于 b 分支，`git merge a`