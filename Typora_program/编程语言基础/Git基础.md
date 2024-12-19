# Git基础

## 1、Git常用命令

## 2、Git分支管理

## 3、Git团队协作

## 4、VSCode集成

## 5、Git遇到的错误

### 错误

- 错误： **git SSL certificate problem: unable to get local issuer certificate**

  > **这个问题是由于没有配置信任的服务器HTTPS验证。默认，[cURL](https://so.csdn.net/so/search?q=cURL&spm=1001.2101.3001.7020)被设为不信任任何CAs，就是说，它不信任任何服务器验证。**

  ```git
  $ git config --global http.sslVerify false
  ```

- 错误：**error: RPC failed; HTTP 502 curl 22 The requested URL returned error: 502 Proxy Error**

  > 这个错误通常意味着 Git 在执行某个操作时无法访问远程服务器，这可能是由于代理错误或网络连接问题引起的。

  ```git
  $ git config --global http.postBuffer 1024000000
  ```

  



## 6.[Pro Git](https://gitee.com/progit/)

```shell
# 简单git命令
$ vim 文件名.后缀               #创建新文件,"i"进入输入模式，输入完成后按"esc"退出，":格式符号"
$ cat 文件名.后缀               #查看文件内容
$ ls                          #展示子文件
$ git status                  #查看状态，是否放入暂存区，绿色为已放入，红色为未放入
$ git rm --cached 文件名.后缀   #删除暂存区中的文件
$ git reflog                  #查看历史操作记录
$ git reset --soft HEAD^      #历史区回退到暂存区
$ git branch 分支名            #创建分支
$ git checkout 分支名          #切换指针到分支，指向分支
```



## 一、走入Git

### 1. Git介绍

   >  Git 是一个开源的<u>分布式版本控制系统</u>，用于敏捷高效的处理任何或大或小的项目
   >
   >  Git 是 Linus Torvalds 为了帮助管理Linux 内核而开发的一个开放源码的版本控制软件。

   

   - 版本控制：

     版本控制（Revision control）是一种在开发的过程中用于管理对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前的版本的软件工程技术。

   - 团队协作：

     从个人作战转变为团队开发

### 2. Git 对比 SVN

   1. **SVN **是<u>**集中式版本控制系统**</u>，版本库是集中放在中央服务器的，而工作的时候，用的都是自己的电脑，所以首先要从中央服务器得到最新的版本，然后工作，完成工作后，需要把自己的代码推送到中央服务器，集中式版本控制系统**必须联网**才能工作
   2. **Git **是<u>**分布式版本库控制系统**</u>，没有中央服务器，每个人的电脑就是一个完整的版本库，工作的时候不需要联网，因为版本都在自己的电脑上，可以离线工作

### 3. Git 安装

   > http://git-scm.com

   验证安装成功

   > 1. 打开`cmd`窗口，输入
   >
   >    ```
   >    git --version
   >    ```
   >
   > 2. 右键打开`Open Git Bash here`，输入
   >
   >    ```
   >    git --version
   >    ```
   >

## 二、Git 常用命令

### 1. 设置用户签名

> 签名的作用就是用来标识用户，以区分不同的开发人员

```shell
git config --global user.email ""
git config --globak user.name ""
```

### 2. 初始化本地库

-  我们希望一个文件夹被`git`管理的话，那么就要在一个文件夹下进行**git 初始化**

- 找到一个希望被`git`管理的文件夹

- 在文件夹内鼠标右键，打开`Open Git Bash here`

- 输入指令

  ```shell
  # git 初始化的指令
  $ git init
  ```

- 然后文件夹内多一个`.git`的文件夹（<u>隐藏文件夹</u>）

- 此时这个文件夹就被`git`管理了，同时包括所有的子文件夹和子文件

- **注意：<u>只有当一个文件夹被`git`管理以后，才可以使用`git`的功能去做版本管理</u>**

  - 只有把某个文件夹授权给`git`
  - `git`才能对文件夹里的内容进行各种操作
  - 而`git init` 就是在进行这个授权的操作

### 3. Git 工作区、暂存区和版本库

工作区 -> 暂存区 -> ->托管平台



**托管平台**

- 局域网（内网）
  - gitlab
- 公网（外网）
  - gitlab
  - github
  - gitee

### 4. git add

- 放入暂存区，使用`gir add`命令

- 把单独一个文件放入暂存区

  ```shell
  # 把文件下的 index.tex 文本放入缓存区
  $ git add index.tex
  ```

- 把单独一个文件夹放入暂存区（暂存区不能存放空文件夹）

  ```shell
  # 把文件夹下的 ceshi 文件夹放入暂存区
  $ git add ceshi/
  ```

- 把所有文件都放入暂存区

  ```shell
  # 把文件夹下的所有内容放入暂存区
  $ git add --all
  
  # git add --all 简单写法
  $ git add .
  ```

  - 全部存放时两个命令均可

### 5. git commit

```shell
# 把暂存区的内容放入历史区
$ git commit -m "解释文本"
```

使用`git log`指令查看版本信息

```shell
# 查看当前历史区版本信息
$ git log
```

- 使用`git reset --hard 版本编号`进行历史回退

  ```shell
  # 回退到上一次提交的版本
  $ git reset --hard HEAD^
  
  # 回退到上上次提交的版本
  $ git reset --hard HEAD^^
  $ git reset --hard HEAD~2
  ```


### 6. git revert 与 git reset

- `git reset` 是回滚到对应的`commit-id`，相当于是删除了`commit-id` 以后的所有提交，并且不会产生新的`commit-id` 记录，如果要推送到远程服务器的话，需要强制推送`-f`
- `git revert` 是反做撤销其中的`commit-id`，然后重新生成一个`commit-id`。本身不会对其他的提交`commit-id` 产生影响，如果要推送到远程服务器的话，就是普通的操作`git push`。

## 三、Git 分支

1. **初识分支**

   - `git` 分支，即自己把文件夹分成一个一个独立的区域
   - 每一个功能都是一个独立的分支
   - `git` 在初始化的时候，会自动生成一个分支，叫做`master`，表示主要分支
   - 可以自己开辟多个分支

2. **创建分支**

   - 开辟一个分支使用`git branch 分支名称` 指令

     ```shell 
     # 开辟一个 login 分支
     $ git branch login
     ```

   - 查看当前分支情况

     ```shell
     # 查看当前分支情况
     $ git branch
     ```

     
