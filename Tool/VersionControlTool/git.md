# git
## 安装
- for Windows

  直接去[官网](https://git-scm.com/download/win)下载安装包，安装；

- for Mac

  直接去[官网](https://git-scm.com/download/mac)下载安装包，安装；



## git 操作命令

### 查看
- 查看git版本

  ```shell
  $ git --version
  ```

- 查看公钥

  ```shell
  $ cat ~/.ssh/id_rsa.pub
  ```

- 查看所有远程主机

  ```shell
  $ git remote
  ```

- 查看所有远程主机地址

  ```shell
  $ git remote -v
  ```

- 查看当前状态

  ```shell
  $ git status
  ```

- 查看当前分支

  ```shell
  $ git branch
  ```

- 查看本地已经同步的远程分支

  ```shell
  $ git branch -r
  ```

- 查看所有分支

  ```shell
  $ git branch -a
  ```

- 对比本地和远程

  ```shell
  $ git diff master origin/master
  ```

- 显示出所有有差异的文件列表

  ```shell
  $ git diff <branch1> <branch2> --stat
  ```

- 显示指定文件的详细差异

  ```shell
  $ git diff <branch1> <branch2> 文件名(带路径)
  ```

- 显示出所有有差异的文件的详细差异

  ```shell
  $ git diff <branch1> <branch2>
  ```

- 查看日志

  ```shell
  $ git log
  ```

- 查看当前分支合并记录

  ```shell
  $ git log --graph
  ```

- 查看所有版本（包括被回滚的版本）

  ```shell
  $ git log --reflog
  ```

- 查看dev分支有，master分支中没有的

  ```shell
  $ git log <dev> ^<master>
  ```

- 查看master分支有，dev分支中没有的

  ```shell
  $ git log <master> ^<dev>
  ```

- 查看最近一次合并的详细信息

  ```shell
  $ git show
  ```

- 查看指定commit hashID的所有修改

  ```shell
  $ git show <commitid>
  ```

- 查看所有输入过的命令记录

  ```shell
  $ git reflog
  ```



### 创建新的工作区

- 生成ssh公钥，会在该目录下生成一个ssh文件

  ```shell
  $ ssh-keygen -t rsa -C '我的邮箱@163.com'
  ```

- 进入ssh文件 // Windows和Mac都在用户文件夹下

  ```shell
  $ cd .ssh/
  ```

- 查看ssh文件的钥，id_rsa为私钥，id_rsa.pub为公钥

  ```shell
  $ ls -al
  ```

- 复制公钥到git上

- 从git上复制项目的ssh地址

- 下载项目到该文件夹，输入yes

  ```shell
  $ git clone 复制的ssh地址
  ```

- 进入项目目录

  ```shell
  $ cd 项目文件名
  ```

- 创建 gitignore文件，用来设置需要忽略项目里不需要的文件

  ```shell
  $ vim .gitignore
  ```



### 下载

- 需要输入账号密码pull代码前输入

  ```shell
  $ git config --system --unset credential.helper
  ```

- 下载远程git仓库代码

  ```shell
  $ git clone 'git仓库地址'
  ```

- 输入git邮箱账号密码开始下载

- 更新本地代码到最新

  ```shell
  $ git pull
  ```



### 分支

#### 创建分支
> 两种方法创建分支

1. 创建分支同时切换到该分支

   ```shell
   $ git checkout -b <dev>
   ```

2. 先创建分支再切换到该分支
    1. 创建新的分支

       ```shell
       $ git branch <dev>
       ```

    2. 切换到该分支

       ```shell
       $ git checkout <dev>
       ```

#### 关联本地分支和远程分支
> 关联后可以直接`git pull`不需要加远程分支名

```shell
$ git branch --set-upstream-to=origin/dev  dev
```

#### 提交本地最新代码到分支
1. 添加文件到缓存区

  - 添加全部文件

    ```shell
    $ git add .
    ```
  - 添加更新过的文件

    ```shell
    $ git add -u
    ```

  - 添加单个文件

    ```shell
    $ git add 文件路径
    ```

2. 提交到本地分支

   ```shell
   $ git  commit -m '提交备注'
   ```

3. 推送本地分支到远程仓库

   ```shell
   $ git push origin <分支名>
   ```

#### 合并分支

> 将分支最新合并到主分支上

- 切换到主分支

  ```shell
  $ git checkout master
  ```

- 拉取主分支最新代码

  ```shell
  $ git pull
  ```

- 合并分支到主分支

  ```shell
  $ git merge <分支名>
  ```

> 将主分支最近合并到分支上

- 切换到主分支

  ```shell
  $ git checkout master
  ```

- 拉取主分支最新代码

  ```shell
  $ git pull
  ```

- 切换到分支

  ```shell
  $ git checkout <分支名>
  ```

- 合并主分支最新到分支

  ```shell
  $ git merge master
  ```

##### git merge命令

> 

```shell
$ git merge --no-ff
```



> 

```shell
$ git merge --squash
```



#### 删除分支

- 删除本地分支

  ```shell
  $ git branch -d
  ```

- 删除远程分支

  ```shell
  $ git push origin --delete <分支名>
  ```

####冲突 

##### 查看状态

  ```shell
$ git status
  ```

##### 解决冲突

- 自己分支合并到主分支时有冲突

  > 正常提交

  ```shell
  $ git add .
  ```

  ```shell
  $ git commit -m 'description'
  ```

  ```shell
  $ git push origin yourBranchName
  ```

  - 发起请求 & 切换到目标分支合并自己的分支版本
    - 在git仓库网址内申请 自己分支 -> 目标分支 merge 合并；

    或者

    - 切换到目标分支拉去自己分支（不推荐）

      ```shell
      $ git checkout master
      ```

      ```shell
      $ git merge yourBranchName
      ```

  - **产生冲突**

    - 先切换到目标分支拉去远端最新（切换前切记提交自己分支代码）

      ```shell
      $ git checkout master
      ```

      ```shell
      $ git pull
      ```

    - 回到自己分支

      ```shell
      $ git checkout yourBranchName
      ```

    - 将目标分支合并到自己分支（此时提示有冲突）

      ```shell
      $ git merge master
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

      ```shell
      $ git add .
      ```

      ```shell
      $ git commit -m 'merge'
      ```

      ```shell
      $ git push origin yourBranchName
      ```

    - 再次合并（此时没有冲突，成功合并）

#### 版本回滚

> 撤销上一次 commit 至本地

  ```shell
$ git reset --hard HEAD^
  ```

> 取消回滚/回滚到指定版本

  ```shell
$ git reset --hard commit_id // 上一次提交的commit_id，甚至任何一次提交的commit_id
  ```



#### 更换仓库名称

  ```shell
$ git branch -m old_branch new_branch
  ```

  ```shell
$ git push origin :old_branch
  ```

  ```shell
$ git push --set-upstream origin new_branch
  ```



### 自定义Git（高级技巧）

#### 忽略特殊文件

创建文件 .gitignore

```
# git上传忽略文件
# 日志文件
logs
*.logs

# Mac系统上存储文件夹信息的
.DS_Store

# 依赖包
node_modules/

# 打包文件
dist
```

对已经提交过的文件，忽略规则会无效，需要拉取远端最新代码将文件删除后再提交到远端，同时清除git本地缓存

git清除本地缓存命令如下：

```shell
`git ``rm` `-r --cached .``git add .``git commit -m ``'update .gitignore'`
```

#### 配置命令缩写

- 告诉Git，以后`st`表示`status`：

  ```shell
  $ git config --global alias.st status // --global 全局所有仓库都适用
  ```

#### 将本地git仓库关联到远端

- 在本地初始化项目

  ```shell
  git init
  ```

- 添加到本地仓库

  ```shell
  git add .
  ```

- 提交到本地仓库

  ```shell
  git commit -m ''
  ```

- 在远端仓库设置好秘钥，新建远端仓库

- 关联本地仓库到远端

  ```
  git remote rm origin // 如果提示远端已存在
  git remote add orgin https://github.com/xxx.git
  ```

- 提交本地到远端

  ```shell
  git push -u origin master
  ```




#### 搭建Git服务器

- 拉取 gh-pages 分支

  ```shell
  git checkout gh-pages
  ```

- 打包需要发布的资源

  ```shell
  git build
  ```

- 将build文件内的所有资源移动到根目录

- 提交

- 进入github，选择 gh-pages 分支，进入设置

- 找到 GitHub Pages 页面选择分支发布

- 访问域名为`https://<yourgitname>.github.io`，可以自定义域名

...

### GitHub 使用技巧

快捷键弹框

```
Shift + /
```



#### 搜索语法

- 按编程语言搜索， xxx language:java
- 按文件或路径搜索，xxx in:readme
- 按文件大小搜索，xxx size:>100
- 按地域搜索， xxx location:chengdu
- 按是否fork过搜索，xxx fork:true
- 按照拥有者或者组织搜索，xxx user:yrzx404 或者 xxx org:github
- 按stars数量搜索，xxx stars:>1000
- 按主题搜索，xxx topic:java













git remote prune origin

### 

