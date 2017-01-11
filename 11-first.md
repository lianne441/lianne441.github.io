---
layout: default
title: Blogging Like a Hacker
---


###　笔记



  １. 注册github，登录

   用户名：lianne441.github.io

   邮箱：suiliyan441@sina.cn

   Github 就提供了markdown编译环境

   > Github 上我们的项目中，有一个文件叫 README.md,在这个文件中写markdown就可以编译成html，注意，添加内容的文件名，无所谓，但是后缀一定要 .md 不然无法编译成功

   编辑器中有语法高亮，在页面中字体颜色不受影响，一个颜色显示

　 lianne441.github.io 仓库中使用 markdown,如果想要新增一个html文件，就新增一个md文件，但是这个md文件必须有头部，格式为
　 ---
  title: 我的这篇文章的标题
  ---
  头部与正文要空一行
  头部格式必须正确，影响上传

  ### 第一篇第一个大标题
  上面:后面留一个空格，头部下方留出一个空行，然后再写 markdown 正文

  2. Linux 系统有多种发行版,例如:Red Hat ，Suse，Fedora , CentOS 等

    Ctrl-Alt-T打开命令行

    bash：人名＋命令行

    主要有以下几种操作：
    ls 列出当前位置所有文件
    rm 删除文件，或者文件夹
    cd 改变当前位置
    mv 移动文件
    等等等等

    cd Desktop
    mkdir FolderName
    上面 cd Desktop 改变当前位置到桌面。
    mkdir 是创建名为FolderName一个文件夹的命令

    Linus 是芬兰人，他父亲是政治家（共产主义者）。Linus 在大二的时候创作 Linux 操作系统。69年出生，今天依然在写代码。Linus 的另外一个作品，就是 Git 。

  ３. Linux 这里其实更简单。所有的文件夹都会存在一个顶级老祖宗文件夹之内。这个老祖宗的名字叫做 / 。

  用户主目录 /home/lianne441,外号：～,用户登陆进系统之后，默认的着陆位置就是这个文件夹

  ls  列出当前文件夹下有多少子文件或文件夹

  cd ..
  其中 .. 就是上一级文件夹的外号。

  cd ~
  或者

  cd  
  都可以。

  绝对路径的特点是一定以老祖宗文件夹打头，也就是以 / 打头。

  cd /home/peter
  可以直接跳转到用户主目录。

  Tab 补齐
  敲出文件夹的打头的字母，然后敲 Tab （或者敲两下 Tab ）就可以自动补齐出完整的文件名了

  ４. 文件创建：atom/touch
  文件夹创建： mkdir
  文件夹删除：rm -r folder
  文件移动： mv file ../
  文件删除： rm file
  创建文件或者文件夹

  mkdir project　　新建一个文件夹
    cd project　　跳转到新建文件夹

　touch fileName　新建一个文件

　atom . 用atom打开当前文件夹或文件

  rm fileName
  删除一个文件夹

  rm -r folderName
  移动

  移动用到的是 mv 命令

  mv 被移动的文件或者文件夹的路径  目标文件夹位置
  重命名

  mv 被移动的文件或者文件夹的路径  不存在的位置/文件名
  这样进行的就是原来文件的重命名操作。

  cp 被拷贝的的文件  目标位置
  拷贝文件夹

  cp -r 被拷贝的的文件夹 目标位置
  操作案例

  把 aaa/ 文件夹中的所有文件，都拷贝到 bbb 文件夹中
  $ ls aaa
  aa bb cc
  $ ls bbb
  $ mv  aaa/* bbb
  $ ls aaa
  $ ls bbb
  aa bb cc

　普通用户和超级用户
  sudo rm fileName
  上面的命令可以用超级用户权限来执行一个命令。

  sudo su
  可以直接化身超级用户。

  $ sudo su
  $ whoami
  root
  $ exit
  $ whoami
  peter

  ５. 在 Web 开发领域，最受高手追捧的是三款编辑器：vim ，sublime ，atom 。

  默认就是用 Ctrl-n ，保存用 Ctrl-s 。

  h1<tab> 就自动补齐成<h1></h1>
  这个需要安装一个包叫做 emmet 。

  使用 Ctrl-Shift-P 打开命令面板，然后搜索

  install packages
  可以搜到 Install Packages And Themes ，选中，回车，就进入了装包界面。

  搜索报名，例如 emmet open in browser，搜到之后，点 install 就可以了。

  查看 atom 中已经安装了哪些包，就用 Ctrl-Shift-P 打开命令面板，然后输入

  Uninstall Packages
  就可以看到所有已经安装的包了。

  6.   Git 和 Github 是两个东西,git是软件，linus;github是网站，Tom

  通常我们的 Github 工作流是这样的：

  第一步，在我们自己的笔记本上安装 Atom 和 Git
  第二步，注册 Github 账号，并开启新仓库
  第三步，在笔记本上做代码开发
  第四步，通过 git push 命令来上传代码到 Github

　安装git
  sudo apt-get update
  sudo apt-get install git

  git --version
  如果可以正确输出版本号，证明 Git 已经装好了

  7.   Git 本地工作流（没有网络操作）可以分为以下几步：
  第一步，使用 atom 创建并编辑项目
  第二步，使用 git init 命令，把一个普通项目变成一个Git 仓库
  第三步，使用 git add -A 命令，添加修改内容到 Git
  第四步，使用 git commit -m"my commit msg" 命令，制作一个版本

  mkdir trygit
  然后进入项目，开始添加一个 index.html 文件

  cd trygit
  atom .
  现在我们来把一个普通项目变成一个仓库 ，需要执行

  $ git init

  要查看隐藏文件夹，可以敲

  ls -a
  这样可以看到输出中包含 .git 文件夹了。
  首先来添加修改到 git ：

  git add -A
  注： -A 的意思是添加“所有当前修改内容”

  要想把添加的内容制作成版本，还需要执行

  git commit -m"I add a file"
  注： commit 的意思是”做一件很重要的事”，但是在 git 这里，它的意思就是版本 。-m 就是 message 的简写，后面的内容是再版留言 。

  问题来了，新用户首次执行上面的命令，会看到下面的报错信息


  please tell me who you are
  解决方法是，运行下面的命令

  git config --global user.name  "Peter Wang"
  git config --global user.email  "happypeter1983@gmail.com"
  来设置用户名和邮箱。这样再次执行

  $ git commit -m"I add a file"
  [master (root-commit) dcb0329] I add index.html
   1 file changed, 1 insertion(+)
   create mode 100644 index.html
  就可以成功制作一个版本了。也就是 Git 本地工作流就完成了一个完整的循环。

  后续如果再做第二第三个版本，就是只需要：

  修改内容用 atom
  git add -A
  git commit -m”msg”

  注：git init只需要执行一次就行了

  git log 　　-plog 是日志的意思。-p 是 patch （补丁，也就是修改内容）的缩写。

  小技巧：q 可以退出 git log -p 的界面，敲 j 可以往下翻，敲 k 可以往上翻。

  ８. 点 Settings（设置）这一个标签。打开的页面底部有一个 “Delete this repository” 按钮，意思是”删除这个仓库“，点击按钮。打开的界面中，输入一下这个仓库的名字 happypeter.github.io 就可以把这个仓库删除了。

  第一步：创建本地项目

  mkdir happypeter.github.io

 第二步：创建 github.com 上的同名仓库

 创建完成之后，页面上有两个选择，其中第二个是

 or push an existing repository from the command line

 上传方式有两种 HTTPS 和 SSH ，我们推荐的方式是 SSH，点一下页面上 SSH 字样的按钮。

 cd happypeter.github.io

 git remote add origin git@github.com:funnydeer/funnydeer.github.io.git
 git push -u origin master

   git@github.com:funnydeer/funnydeer.github.io.git

   git push -u origin master

 在本地机器上生成一对 ssh key ，一个公钥，一个私钥

 Jekyll 框架

 首先打开所有的 .md 中的头部改成这样

 ---
 title: First Page
 layout: default
 ---

 然后来创建布局文件 default.html ，这个文件必须存放到 _layouts 文件夹之内，

 _layouts/default.html 内容如下，可以参考我的其他项目中的写法。例如：

 anything anything
   content
 anything anything
 注意，上面的 content 外面要套两个大括号。

 git clone git@github.com:happypeter/digicity.git
 clone 的特点就是不仅仅可以得到最新代码，而且可以得到整个改版历史。而普通下载只能得到最新版本。

 git push 把本地仓库中有，而远端对应仓库中没有的版本推送到远端
 git pull 把远端仓库中有，而本地对应仓库中没有的版本拉到本地
 git clone 把远端仓库，克隆到本地
