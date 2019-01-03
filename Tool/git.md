# git
## 安装
- for Windows

  直接去[官网](https://git-scm.com/download/win)下载安装包，安装；

- for Mac

  直接去[官网](https://git-scm.com/download/mac)下载安装包，安装；



## git 操作命令

### 查看
- 查看公钥

  ```
  cat ~/.ssh/id_rsa.pub
  ```

- 查看所有远程主机

  ```
  git remote
  ```

- 查看所有远程主机地址

  ```
  git remote -v
  ```

- 查看当前状态

  ```
  git status
  ```

- 查看当前分支

  ```
  git branch
  ```

- 查看本地已经同步的远程分支

  ```
  git branch -r
  ```

- 查看所有分支

  ```
  git branch -a
  ```

- 对比本地和远程

  ```
  git diff master origin/master
  ```

- 显示出所有有差异的文件列表

  ```
  git diff <branch1> <branch2> --stat
  ```

- 显示指定文件的详细差异

  ```
  git diff <branch1> <branch2> 文件名(带路径)
  ```

- 显示出所有有差异的文件的详细差异

  ```
  git diff <branch1> <branch2>
  ```

- 查看日志

  ```
  git log
  ```

- 查看当前分支合并记录

  ```
  git log --graph
  ```

- 查看所有版本（包括被回滚的版本）

  ```
  git log --reflog
  ```

- 查看dev分支有，master分支中没有的

  ```
  git log <dev> ^<master>
  ```

- 查看master分支有，dev分支中没有的

  ```
  git log <master> ^<dev>
  ```

- 查看最近一次合并的详细信息

  ```
  git show
  ```

- 查看指定commit hashID的所有修改

  ```
  git show <commitid>
  ```

- 查看所有输入过的命令记录

  ```
  git reflog
  ```



### 创建新的工作区

- 生成ssh公钥，会在该目录下生成一个ssh文件

  ```
  ssh-keygen -t rsa -C '我的邮箱@163.com'
  ```

- 进入ssh文件

  ```
  cd .ssh/
  ```

- 查看ssh文件的钥，id_rsa为私钥，id_rsa.pub为公钥

  ```
  ls -al
  ```

- 复制公钥到git上

- 从git上复制项目的ssh地址

- 下载项目到该文件夹，输入yes

  ```
  git clone 复制的ssh地址
  ```

- 进入项目目录

  ```
  cd 项目文件名
  ```

- 创建 gitignore文件，用来设置需要忽略项目里不需要的文件

  ```
  vim .gitignore
  ```



### 下载

- 需要输入账号密码pull代码前输入

  ```
  git config --system --unset credential.helper
  ```

- 下载远程git仓库代码

  ```
  git clone 'git仓库地址' 
  ```

- 输入git邮箱账号密码开始下载

- 更新本地代码到最新

  ```
  git pull
  ```



### 分支

#### 创建分支
> 两种方法创建分支

1. 创建分支同时切换到该分支

   ```
   git checkout -b <dev>
   ```

2. 先创建分支再切换到该分支
    1. 创建新的分支

       ```
       git branch <dev>
       ```

    2. 切换到该分支

       ```
       git checkout <dev>
       ```

#### 关联本地分支和远程分支
> 关联后可以直接`git pull`不需要加远程分支名

```
git branch --set-upstream-to=origin/dev  dev
```

#### 提交本地最新代码到分支
1. 添加文件到缓存区

  - 添加全部文件

    ```
    git add .
    ```
  - 添加更新过的文件

    ```
    git add -u
    ```

  - 添加单个文件

    ```
    git add 文件路径
    ```

2. 提交到本地分支

   ```
   git  commit -m '提交备注'
   ```

3. 推送本地分支到远程仓库

   ```
   git push origin <分支名>
   ```

#### 合并分支

> 将分支最新合并到主分支上

- 切换到主分支

  ```
  git checkout master
  ```

- 拉取主分支最新代码

  ```
  git pull
  ```

- 合并分支到主分支

  ```
  git merge <分支名>
  ```

> 将主分支最近合并到分支上

- 切换到主分支

  ```
  git checkout master
  ```

- 拉取主分支最新代码

  ```
  git pull
  ```

- 切换到分支

  ```
  git checkout <分支名>
  ```

- 合并主分支最新到分支

  ```
  git merge master
  ```

##### git merge命令

> git merge --no-ff

```

```



> git merge --squash

```

```



#### 删除分支

- 删除本地分支

  ```
  git branch -d
  ```

- 删除远程分支

  ```
  git push origin --delete <分支名>
  ```

####冲突 

##### 查看状态

```
git status
```

##### 解决冲突

- 自己分支合并到主分支时有冲突

  > 正常提交

  ```
  git add .
  ```

  ```
  git commit -m 'description'
  ```

  ```
  git push origin yourBranchName
  ```

  - 发起请求 & 切换到目标分支合并自己的分支版本
    - 在git仓库网址内申请 自己分支 -> 目标分支 merge 合并；

    或者

    - 切换到目标分支拉去自己分支（不推荐）

      ```
      git checkout master
      ```

      ```
      git merge yourBranchName
      ```

  - **产生冲突**

    - 先切换到目标分支拉去远端最新（切换前切记提交自己分支代码）

      ```
      git checkout master
      ```

      ```
      git pull
      ```

    - 回到自己分支

      ```
      git checkout yourBranchName
      ```

    - 将目标分支合并到自己分支（此时提示有冲突）

      ```
      git merge master
      ```

    - 打开文件解决冲突

      此时文件内：

      ```
      <<<<<<< HEAD
      文件差异内容（传入）
      =======
      文件差异内容（本地）
      >>>>>>> yourBranchName
      ```

      手动删除 `<<<<<<< HEAD`、 `=======` 、`>>>>>>> yourBranchName`和冲突的内容

    - 再次提交

      ```
      git add .
      ```

      ```
      git commit -m 'merge'
      ```

      ```
      git push origin yourBranchName
      ```

    - 再次合并（此时没有冲突，成功合并）

#### 版本回滚

> 回滚到最近一次的提交前

```
git reset --hard HEAD^
```

> 取消回滚

```
git reset --hard commit_id // 上一次提交的commit_id，甚至任何一次提交的commit_id
```



#### 更换仓库名称

```
git branch -m old_branch new_branch
```

```
git push origin :old_branch
```

```
git push --set-upstream origin new_branch
```



### 自定义Git（高级技巧）

#### 忽略特殊文件

#### 配置命令缩写

- 告诉Git，以后`st`表示`status`：

  ```
  git config --global alias.st status // --global 全局所有仓库都适用
  ```

#### 搭建Git服务器

