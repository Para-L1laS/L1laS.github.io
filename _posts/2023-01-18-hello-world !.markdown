# **建站小记**

## 写在前边

  在每天训练到半夜的人工智能大作业结束后，忽然感觉没什么事做，于是就想着在gayhub上建一个个人博客。整个过程也是不怎么容易（本人忙着参加一战，没时间（）：简单的在[廖雪峰](https://www.liaoxuefeng.com/wiki/896043488029600)老师的网站上学了点git入门，之后在网上找了个Jekyll模板，使用github pages搭建了本站。

## 准备工作

  因为打算使用Jekyll模板，而Jekyll是基于**Ruby**语言开发的，所以要先安装Ruby。其次要注册自己的github账号并建立自己的仓库，用来搭建博客网站。最后要安装git，以便后续链接到远程库以及推送。

- 首先，在github上注册账号，右上角选择**Your respositories**，点击**New**创建一个库，库名设置成**你的github名字.github.io**即可。
- 有关Ruby安装，在窗户平台可以使用**RubyInstaller**，建议找国内网盘链接（不要问我为什么，问就是外网下载每秒几十k的辛酸往事），建议在最后一步勾选默认**UTF-8**格式。
- git安装可以直接去官网下载，右键出现**Git Bash Here**即可。本人使用的git版本为**2.37.1.windows.1**



## Jekyll安装

  Ruby安装完毕之后，打开命令行，使用指令：

> gem install jekyll
>
> gem install jekyll bundle

 安装Jekyll和Jekyll bundle。若安装过程中出现错误（除非你科学上网不然都会报错的hhhhh），可以尝试换gem源。目前默认的源被墙，淘宝的源挂了，腾讯的源流量太大可能挤不进去，可以使用清华的镜像（kali都是在这下的，清华yyds）。若想更换源，可以尝试以下指令：

> gem sources -l  “查看现有源”
>
> gem sources --remove https://rubygems.org/ “删除默认源（可以改remove后的参数）”
>
> gem sources --add https://mirrors.tuna.tsinghua.edu.cn/rubygems/ “添加清华的镜像源”

## 本地库管理

  创建一个文件夹用于容纳模板，右键选择**Git Bash Here**，输入指令 __<font color=red>git init</font> __创建本地库（由于窗户系统的奇奇怪怪的讲究，文件路径最好不要有中文）。之后把找到的模板文件复制到文件夹下，使用以下指令把文件添加到库：

> git add *  “把所有文件添加到暂存区，星号是通配符啦”
>
> git add document  “添加单个文件到暂存区 ”
>
> git commit -m 'message' “把暂存区的文件添加到库，引号内的东西可以理解为’版本更新说明‘”

 在端口4000没有被占用的前提下可以在本地预览效果。首先执行指令 **<font color=red>bundle install</font>**引入引入Bundle来管理项目中的所有Gem依赖。若出现版本兼容问题（<font color=red>can't find gem bundler (>= 0.a)</font>），可以打开下载模板的**<font color=blue>Gemfile.lock</font>**文件，用记事本打开，拉到最后，找到字段**<font color=red>BUNDLED WITH</font>**，把版本改成自己的bundle版本即可。（cmd中输入**<font color=red>bundle -v</font>**即可查看自己安装的版本）

 之后在git bash窗口输入**<font color=red>bundle exec jekyll serve</font>**，浏览器访问链接http://127.0.0.1:4000即可。

## 链接远程库以及推送

  这一步为链接到自己的远程仓库以及文件推送，可以理解为把本地文件上传到服务器的过程。

  在这一步，我们要先创建一个<font color=blue>.ssh</font>文件，然后把公钥添加到自己的github账户上。在git bash窗口下输入指令：

> ssh-keygen -t rsa -c "邮箱地址"    “引号内放入自己的邮箱地址即可”

 之后在用户主目录下找到<font color=blue>.ssh</font>文件，用记事本打开其中的<font color=blue>id_rsa.pub</font>文件（即为rsa公钥密码的公钥），然后去自己github账户下的“**Account settings**”，“**SSH Keys**”，把自己的公钥粘贴上去就可以了。这一步的目的在于对你的计算机进行认证，只有认证之后的计算机才能进行推送等操作。

  认证过后，在进行推送之前要链接到远程库。链接到远程库之后，直接推送即可（github上传到服务器更新可能需要时间）。使用以下指令进行该操作：

> git remote add origin git@github.com:username/yourblog.git   
>
> “username填写你自己账户的名字，斜线后边填写库名。origin为远程库的默认名称（什么[烂橘子]([Electronic Arts 首頁 - EA 官方網站](https://www.ea.com/zh-tw))）”
>
> git push origin master  “这句为推送”



## 有关Jekyll模板

- 修改标题：使用记事本打开本地库路径下的<font color=blue>_config.yml</font>，修改#basic下的文件即可
- 博客更新：博客全都放在<font color=blue>_posts</font>文件夹内，命名格式为**年-月-日-标题.markdown**，推送即可。













