# Git
基本流程:
[Remote] -> fetch/clone( <- push) [Repository] -> checkout ( <- commit  [Stage] <- add ) (pull from Remote) [workspace]
![git流程](https://github.com/org4hzy/hzy-notes/pic/git_chart.png)

* 配置
```
git config --list #显示当前配置
git config --global user.name 'huangzy'
git config --global user.email '123@qq.com'

* 问题 git clone server certificate verification failed *
git config --global http.sslverify false
```

* 新建
```
git init 
git init [project-name]
git clone [url]
```

* 增删
```
git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
git add [directory]

# 添加当前目录的所有文件到暂存区
git add .

# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交
git add -p

git rm [file]

git mv [file-org] [file-renamed]
```

* 提交
```
# 当前目录所有文件 
git commit -a -m "comments ..."

git commit -v 

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
git commit --amend -m "new comments"
```

* 分支
```
#all branchs
git branch -r

#new branch
git branch [branch-name]

#新建一个分支并切换到分支
git checkout -b [branch]

# 合并
git merge [branch] 

# 删除
git branch -d [branch]
git push origin --delete [branch]
git branch -dr [remote/branch]
```

* 标签
```
git tag [tag] [commit]

git tag -d [tag]
```

* 状态
```
git status

git log --pretty=oneline

git show [commit]:[filename]

git reflog

git diff

git shortlog -sn
```

* 远程操作
```
git remote -v

git push --all --force
```

* 撤销
```
git reset --hard [commit]

git stash
git stash pop
```
