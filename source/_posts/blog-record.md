---
title: blog record
date: 2019-12-19 13:39:12
tags:
	- 博客建立日志
categories: 博客
preview_text: 博客运行日志
preview: imgs/preview/preview4.jpg
---
博客运行记录

初始安装步骤
1. 安装node.js
2. 添加阿里国内镜像源加速 npm config set registry https://registry.npm.taobao.org
3. 安装git https://link.zhihu.com/?target=https%3A//git-scm.com/download/win
最后一步添加路径时选择Use Git from the Windows Command Prompt，这样我们就可以直接在命令提示符里打开git了。
安装完成后在命令提示符中输入git --version验证是否安装成功。
4. 注册Github账户，开启github pages
5. 安装Hexo
	a. 在合适的地方新建一个文件夹，用来存放自己的博客文件，比如我的博客文件都存放在D:\study\program\blog目录下。
	b. 在该目录下右键点击Git Bash Here，打开git的控制台窗口，以后我们所有的操作都在git控制台进行，就不要用Windows自带的控制台了。
	c. 定位到该目录下，输入npm i hexo-cli -g安装Hexo。会有几个报错，无视它就行。
	d. 安装完后输入hexo -v验证是否安装成功。
	f. 然后就要初始化我们的网站，输入hexo init初始化文件夹，接着输入npm install安装必备的组件。
	g. 这样本地的网站配置也弄好啦，输入hexo g生成静态网页，然后输入hexo s打开本地服务器，然后浏览器打开http://localhost:4000/.
	
6. 连接Github与本地

	首先右键打开git bash，然后输入下面命令：
	git config --global user.name "godweiyang"
	git config --global user.email "792321264@qq.com"
	用户名和邮箱根据你注册github的信息自行修改。

	然后生成密钥SSH key：
	ssh-keygen -t rsa -C "792321264@qq.com"
	打开github，在头像下面点击settings，再点击SSH and GPG keys，新建一个SSH，名字随便。

	git bash中输入
	cat ~/.ssh/id_rsa.pub
	将输出的内容复制到框中，点击确定保存。

	输入ssh -T git@github.com
	打开博客根目录下的_config.yml文件，这是博客的配置文件，在这里你可以修改与博客相关的各种信息。
	修改最后一行的配置：
	deploy:
	  type: git
	  repository: https://github.com/godweiyang/godweiyang.github.io
	  branch: master
	repository修改为你自己的github项目地址。
7. 写文章、发布文章
	a. 首先在博客根目录下右键打开git bash，安装一个扩展npm i hexo-deployer-git。
	b. 然后输入hexo new post "article title"，新建一篇文章。
	c. 然后打开D:\study\program\blog\source\_posts的目录，可以发现下面多了一个文件夹和一个.md文件，一个用来存放你的图片等数据，另一个就是你的文章文件啦。
	d. 编写完markdown文件后，根目录下输入hexo g生成静态网页，然后输入hexo s可以本地预览效果，最后输入hexo d上传到github上。这时打开你的github.io主页就能看到发布的文章啦。



hexo+git+node.js安装后设置多PC 
1. 设置hexo为默认分支（因为我们只需要手动管理这个分支上的Hexo网站文件）；
2. 使用git clone git@github.com:CrazyMilk/CrazyMilk.github.io.git拷贝仓库；
3. 本地博客的部署文件（Hexo目录下的全部文件）全部拷贝进username.github.io文件目录中去。
接下来，进入username.github.io文件目录下，将该目录下的全部文件提交到xxx分支，提交之前需注意：
将themes目录以内中的主题的.git目录删除（如果有），因为一个git仓库中不能包含另一个git仓库，提交主题文件夹会失败。
可能有人会问，删除了themes目录中的.git不就不能git pull更新主题了吗，很简单，需要更新主题时在另一个地方git clone下来该主题的最新版本，然后将内容拷到当前主题目录即可
4. 执行git add .、git commit -m 'back up hexo files'（引号内容可改）、git push即可将博客的hexo部署环境提交到GitHub个人仓库的xxx分支。


新电脑同步更改blog
1. 将新电脑的生成的ssh key添加到GitHub账户上
2. 在新电脑上克隆username.github.io仓库的xxx分支到本地，此时本地git仓库处于xxx分支
3. 切换到username.github.io目录，执行npm install(由于仓库有一个.gitignore文件，里面默认是忽略掉 node_modules文件夹的，也就是说仓库的hexo分支并没有存储该目录[也不需要]，所以需要install下)

编辑、撰写文章或其他博客更新改动
依次执行git add .、git commit -m 'back up hexo files'（引号内容可改）、git push指令，保证xxx分支版本最新
执行hexo d -g指令（在此之前，有时可能需要执行hexo clean），完成后就会发现，最新改动已经更新到master分支了，两个分支互不干扰！
注意： 每次换电脑进行博客更新时，不管上次在其他电脑有没有更新，最好先git pull **

更换主题为gal
thanks: https://github.com/ZEROKISEKI/hexo-theme-gal
