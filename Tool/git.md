# git
## 安装
- for Windows

  直接去官网下载安装包，安装；

- for Mac

  直接去官网下载安装包，安装；

## git 操作命令

> 查看
```
cat ~/.ssh/id_rsa.pub    //查看公钥
git remote        //查看所有远程主机
git remote -v    //查看所有远程主机地址
git status        //查看当前状态
git branch    //查看当前分支
git branch -r    //查看本地已经同步的远程分支
git branch -a    //查看所有分支
git diff master origin/master    //对比本地和远程
git diff <branch1> <branch2> --stat    //显示出所有有差异的文件列表
git diff <branch1> <branch2> 文件名(带路径)    //显示指定文件的详细差异
git diff <branch1> <branch2>    //显示出所有有差异的文件的详细差异
git log    //查看日志
git log --graph    //查看当前分支合并记录
git log <dev> ^<master>    //查看dev分支有，master分支中没有的
git log <master> ^<dev>    //查看master分支有，dev分支中没有的
git show    //查看最近一次合并的详细信息
git show <commitid>    //查看指定commit hashID的所有修改
```

> 创建新的工作区
//生成ssh公钥，会在该目录下生成一个ssh文件
```
ssh-keygen -t rsa -C '我的邮箱@163.com'
```

//进入ssh文件
```
cd .ssh/
```

//查看ssh文件的钥，id_rsa为私钥，id_rsa.pub为公钥
```
ls -al
```

复制公钥到git上

从git上复制项目的ssh地址

//下载项目到该文件夹，输入yes
```
git clone 复制的ssh地址
```

//进入项目目录
```
cd 项目文件名
```

//创建 gitignore文件，用来设置需要忽略项目里不需要的文件
```
vim .gitignore
```
