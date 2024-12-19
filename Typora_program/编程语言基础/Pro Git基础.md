# Pro Git基础

[Pro Git（中文版） (gitee.com)](https://gitee.com/progit/)

## 1.起步

### 1.1关于版本控制(VCS)

> 版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统

- 本地版本控制系统

- 集中化版本控制系统

  > 集中化的版本控制系统（Centralized Version Control Systems，简称 CVCS）,都有一个**单一的集中管理的服务器**，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新

- 分布式版本控制系统

  > 分布式版本控制系统（Distributed Version Control System，简称 DVCS）,客户端并不只提取最新版本的文件快照，而是把代码仓库完整地镜像下来,事后都可以用任何一个镜像出来的本地仓库恢复

### 1.2Git简史

同生活中的许多伟大事物一样，Git 诞生于一个极富纷争大举创新的年代。

Linux 内核开源项目有着为数众广的参与者。 绝大多数的 Linux 内核维护工作都花在了提交补丁和保存归档的繁琐事务上（1991－2002年间）。 到 2002 年，整个项目组开始启用一个专有的分布式版本控制系统 *`BitKeeper`* 来管理和维护代码。

到了 2005 年，开发 *`BitKeeper`* 的商业公司同 Linux 内核开源社区的合作关系结束，他们收回了 Linux 内核社区免费使用 *`BitKeeper`* 的权力。 这就迫使 Linux 开源社区（特别是 Linux 的缔造者 Linus Torvalds）基于使用 *`BitKeeper`* 时的经验教训，开发出自己的版本系统。 他们对新的系统制订了若干目标：

- 速度
- 简单的设计
- 对非线性开发模式的强力支持（允许成千上万个并行开发的分支）
- 完全分布式
- 有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）

自诞生于 2005 年以来，Git 日臻成熟完善，在高度易用的同时，仍然保留着初期设定的目标。 它的速度飞快，极其适合管理大项目，有着令人难以置信的非线性分支管理系统（参见 [Git 分支](https://www.progit.cn/#_git_branching)）。

### 1.3Git基础

- #### 直接记录快照，而非差异比较

  > `Git` 更像是把数据看作是对小型文件系统的一组快照。 每次你提交更新，或在 `Git` 中保存项目状态时，它主要对当时的全部文件制作一个快照并保存这个快照的索引。 为了高效，如果文件没有修改，`Git `不再重新存储该文件，而是只保留一个链接指向之前存储的文件

- #### 近乎所有操作都是本地执行

  > 在 `Git `中的绝大多数操作都只需要访问本地文件和资源，一般不需要来自网络上其它计算机的信息

- #### Git 保证完整性

  > `Git `中所有数据在存储前都计算校验和，然后以校验和来引用
  >
  > `Git` 用以计算校验和的机制叫做 **`SHA-1`** 散列（**hash**，哈希）。 这是一个由 **40 **个十六进制字符（**0-9 **和 **a-f**）组成字符串，基于 `Git `中文件的内容或目录结构计算出来

- #### Git 一般只添加数据

  > 你执行的 Git 操作，几乎只往 Git 数据库中增加数据。 很难让 Git 执行任何不可逆操作，或者让它以任何方式清除数据

- #### 三种状态

  - 已提交（committed）：已提交表示数据已经安全的保存在**本地数据库**中
  - 已修改（modified）：已修改表示修改了文件，但还**没保存到数据库**中
  - 已暂存（staged）：已暂存表示对一个已修改文件的当前版本做了标记，使之**包含在下次提交的快照中**

- ### 三个工作区域

  - **Git 仓库:**Git 仓库目录是 Git 用来保存项目的元数据和对象数据库的地方。 这是 Git 中最重要的部分，从其它计算机克隆仓库时，拷贝的就是这里的数据
  - **工作目录:**工作目录是对项目的某个版本独立提取出来的内容
  - **暂存区域:**暂存区域是一个文件，保存了下次将提交的文件列表信息，一般在 Git 仓库目录中
  - ![](https://www.progit.cn/images/areas.png)

- ### 基本的 Git 工作流程如下：

  1. 在工作目录中修改文件。

  2. 暂存文件，将文件的快照放入暂存区域。

  3. 提交更新，找到暂存区域的文件，将快照永久性存储到 Git 仓库目录

### 1.4命令行

> Git 有多种使用方式。 你可以使用原生的命令行模式，也可以使用 GUI 模式，这些 GUI 软件也能提供多种功能

### 1.5安装Git

**[Git](http://git-scm.com/download/win)**

### 1.6初次运行 Git 前的配置

Git 自带一个 `git config` 的工具来帮助设置控制 Git 外观和行为的配置变量。 这些变量存储在三个不同的位置：

1. `/etc/gitconfig` 文件: 包含系统上每一个用户及他们仓库的通用配置。 如果使用带有 `--system` 选项的 `git config` 时，它会从此文件读写配置变量。
2. `~/.gitconfig` 或 `~/.config/git/config` 文件：只针对当前用户。 可以传递 `--global` 选项让 Git 读写此文件。
3. 当前使用仓库的 Git 目录中的 `config` 文件（就是 `.git/config`）：针对该仓库。

每一个级别覆盖上一级别的配置，所以 `.git/config` 的配置变量会覆盖 `/etc/gitconfig` 中的配置变量。

在 Windows 系统中，Git 会查找 `$HOME` 目录下（一般情况下是 `C:\Users\$USER`）的 `.gitconfig` 文件。 Git 同样也会寻找 `/etc/gitconfig` 文件，但只限于 MSys 的根目录下，即安装 Git 时所选的目标位置。

### 1.7用户信息

安装完 Git 应该做的第一件事就是设置你的用户名称与邮件地址。 这样做很重要，因为每一个 Git 的提交都会使用这些信息，并且它会写入到你的每一次提交中，不可更改：

```git
$ git config --global user.name "example"
$ git config --global user.email example@example.com
```

如果使用了 `--global` 选项，那么该命令只需要运行一次，因为之后无论你在该系统上做任何事情， Git 都会使用那些信息

### 1.8文本编辑器

用户信息已经设置完毕，你可以配置默认文本编辑器了，当 Git 需要你输入信息时会调用它。 如果未配置，Git 会使用操作系统默认的文本编辑器，通常是 Vim。 如果你想使用不同的文本编辑器，例如 Emacs，可以这样做：

```git
$ git config --global core.editor emacs
```

### 1.9检查配置信息

- 如果想要检查你的配置，可以使用 `git config --list` 命令来列出所有 Git 当时能找到的配置

    ```git
    $ git config --list
    ```
    
    可能会看到重复的变量名，因为 Git 会<u>从不同的文件中读取同一个配置</u>
    
- 可以通过输入 `git config <key>`： 来检查 Git 的某一项配置

    ```git
    $ git config user.name
    ```

### 1.10获取帮助

三种方法可以找到 Git 命令的使用手册：

```git
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
```

## 2. Git 基础

### 2.1获取 Git 仓库

1. 在现有项目或目录下导入所有文件到 Git 中
2. 从一个服务器克隆一个现有的 Git 仓库

#### 2.1.1在现有目录中初始化仓库

如果你打算使用 Git 来对现有的项目进行管理，你只需要进入该项目目录并输入：

```git
$ git init
```

该命令将创建一个名为 `.git` 的子目录，这个子目录含有你初始化的 Git 仓库中所有的必须文件，这些文件是 Git 仓库的骨干。 但是，在这个时候，我们仅仅是做了一个初始化的操作，你的项目里的文件还没有被跟踪



如果你是在一个已经存在文件的文件夹（而不是空文件夹）中初始化 Git 仓库来进行版本控制的话，你应该开始跟踪这些文件并提交。 你可通过 `git add` 命令来实现对指定文件的跟踪，然后执行 `git commit` 提交

```git
$ git add *.c
$ git add LICENSE
$ git commit -m 'initial project version'
```

#### 2.1.2克隆现有的仓库

Git 克隆的是该 Git 仓库服务器上的几乎所有数据，而不是仅仅复制完成你的工作所需要文件。 当你执行 `git clone` 命令的时候，默认配置下远程 Git 仓库中的每一个文件的每一个版本都将被拉取下来



克隆仓库的命令格式是 `git clone [url]` 。 比如，要克隆 Git 的可链接库 libgit2，可以用下面的命令：

```git
$ git clone https://github.com/libgit2/libgit2
```



如果你想在克隆远程仓库的时候，自定义本地仓库的名字，你可以使用如下命令：

```git
$ git clone https://github.com/libgit2/libgit2 `rename`
```

### 2.2记录每次更新到仓库

工作目录下的每一个文件都不外乎这两种状态：已跟踪或未跟踪。 已跟踪的文件是指那些被纳入了版本控制的文件，在上一次快照中有它们的记录，在工作一段时间后，它们的状态可能处于未修改，已修改或已放入暂存区。 工作目录中除已跟踪文件以外的所有其它文件都属于未跟踪文件，它们既不存在于上次快照的记录中，也没有放入暂存区。 初次克隆某个仓库的时候，工作目录中的所有文件都属于已跟踪文件，并处于未修改状态



使用 Git 时文件的生命周期如下：

![](https://www.progit.cn/images/lifecycle.png)

### 2.3检查当前文件状态

要查看哪些文件处于什么状态，可以用 `git status` 命令,如果在克隆仓库后立即使用此命令，会看到类似这样的输出：

```git
$ git status
On branch master
nothing to commit, working directory clean
```



让我们在项目下创建一个新的 README 文件。 如果之前并不存在这个文件，使用 `git status` 命令，你将看到一个新的未跟踪文件：

```git
$ echo 'My Project' > README
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README

nothing added to commit but untracked files present (use "git add" to track)
```

### 2.4跟踪新文件

使用命令 `git add` 开始跟踪一个文件。 所以，要跟踪 README 文件，运行：

```console
$ git add README
```

此时再运行 `git status` 命令，会看到 README 文件已被跟踪，并处于暂存状态：

```console
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README
```

### 2.5暂存已修改文件

现在我们来修改一个已被跟踪的文件。 如果你修改了一个名为 `CONTRIBUTING.md` 的已被跟踪的文件，然后运行 `git status` 命令，会看到下面内容：

```console
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   README

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   CONTRIBUTING.md
```

要暂存这次更新，需要运行 `git add` 命令。 这是个多功能命令：可以用它开始跟踪新文件，或者把已跟踪的文件放到暂存区，还能用于合并时把有冲突的文件标记为已解决状态等。 将这个命令理解为“添加内容到下一次提交中”而不是“将一个文件添加到项目中”要更加合适。

### 2.6状态简览

#### 状态简览

`git status` 命令的输出十分详细，但其用语有些繁琐。 如果你使用 `git status -s` 命令或 `git status --short` 命令，你将得到一种更为紧凑的格式输出。 运行 `git status -s` ，状态报告输出如下：

```console
$ git status -s
 M README
MM Rakefile
A  lib/git.rb
M  lib/simplegit.rb
?? LICENSE.txt
```

- 新添加的未跟踪文件前面有 `??` 标记，
- 新添加到暂存区中的文件前面有 `A` 标记，
- 修改过的文件前面有 `M` 标记。 
- 你可能注意到了 `M` 有两个可以出现的位置，出现在右边的 `M` 表示该文件被修改了但是还没放入暂存区，出现在靠左边的 `M` 表示该文件被修改了并放入了暂存区。 
- 例如，上面的状态报告显示： `README` 文件在工作区被修改了但是还没有将修改后的文件放入暂存区,`lib/simplegit.rb` 文件被修改了并将修改后的文件放入了暂存区。 而 `Rakefile` 在工作区被修改并提交到暂存区后又在工作区中被修改了，所以在暂存区和工作区都有该文件被修改了的记录

### 2.7忽略文件

一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。

在这种情况下，我们可以创建一个名为 `.gitignore` 的文件，列出要忽略的文件模式

```console
$ cat .gitignore
*.[oa]
*~
```

第一行告诉 Git 忽略所有以 `.o` 或 `.a` 结尾的文件。一般这类对象文件和存档文件都是编译过程中出现的。 第二行告诉 Git 忽略所有以波浪符（~）结尾的文件，许多文本编辑软件（比如 Emacs）都用这样的文件名保存副本。 此外，你可能还需要忽略 log，tmp 或者 pid 目录，以及自动生成的文档等等。 要养成一开始就设置好 .gitignore 文件的习惯，以免将来误提交这类无用的文件。

文件 `.gitignore` 的格式规范如下：

- 所有空行或者以 `＃` 开头的行都会被 Git 忽略。
- 可以使用标准的 glob 模式匹配。
- 匹配模式可以以（`/`）开头防止递归。
- 匹配模式可以以（`/`）结尾指定目录。
- 要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（`!`）取反。

所谓的 glob 模式是指 shell 所使用的简化了的正则表达式。 星号（`*`）匹配零个或多个任意字符；`[abc]` 匹配任何一个列在方括号中的字符（这个例子要么匹配一个 a，要么匹配一个 b，要么匹配一个 c）；问号（`?`）只匹配一个任意字符；如果在方括号中使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配（比如 `[0-9]` 表示匹配所有 0 到 9 的数字）。 使用两个星号（`*`) 表示匹配任意中间目录，比如`a/**/z` 可以匹配 `a/z`, `a/b/z` 或 `a/b/c/z`等。

我们再看一个 .gitignore 文件的例子：

```
# no .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in the build/ directory
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory
doc/**/*.pdf
```

| TIP  | GitHub 有一个十分详细的针对数十种项目及语言的 `.gitignore` 文件列表，你可以在 https://github.com/github/gitignore 找到它. |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

### 2.8查看已暂存和未暂存的修改

