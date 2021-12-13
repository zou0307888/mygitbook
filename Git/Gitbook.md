<!--
 * @Author: Lily
 * @Date: 2021-12-09 14:48:23
 * @LastEditors: Lily
 * @LastEditTime: 2021-12-13 17:35:23
-->
# Gitbook

## 本地配置Gitbook，部署Gitbook到Github

# Nodejs安装及环境配置
官网下载nodejs并正常安装：https://nodejs.org/en/

执行命令node -v查看node版本

  node -v

最新版的node在安装时同时也安装了npm,执行npm -v查看npm版本

  npm -v

# 修改全局依赖包下载路径

  参考资料：https://www.cnblogs.com/liuqiyun/p/8133904.html

1.安装路径下创建完两个空文件夹：node_global，node_cache

2.打开cmd窗口命令，输入

  npm config set prefix "安装路径\node_global"
  npm config set cache "安装路径\node_cache"

1.设置环境变量：我的电脑”-右键-“属性”-“高级系统设置”-“高级”-“环境变量”。

2.在【系统变量】下新建【NODE_PATH】，输入【安装路径\node_global\node_modules】

3.在【用户变量】下的【Path】修改为【安装路径\node_global】

4.配置完后，安装个module测试下，我们就安装最常用的express模块，cmd输入命令（需要管理运行）：

  npm install express -g     # -g是全局安装的意思

# GitBook本地安装和设置

1.安装gitbook，cmd输入命令（需要管理运行）:

  npm install gitbook-cli -g

2.创建一个文件夹，需要初始化目录，cmd输入命令（需要管理运行）:

  gitbook init

3.检查文件，生成README.md 和 SUMMARY.md文件

4.编辑SUMMARY.md，增加类似目录

  #Summary
    * [Introduction](README.md)
    * [Python](python/README.md)
    * [Git](Git/README.md)
    * [GitBash](Git/GitBash.md)
    * [GitBook](Git/GitBook.md)
    * [Pytest](Pytest/README.md)   
5.重新更新目录（每次更新目录都要重新更新目录），cmd输入命令（需要管理运行） 

  gitbook init

6.打开本地服务器

  gitbook serve

7.浏览器访问：http://localhost:4000

# 把Gitbook部署到Github

参考资料：https://www.jianshu.com/p/4e109a1113b2?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation

1.Github新建一个仓库

2.Git bash访问gitbook目录（前面步骤已经创建），执行一下命令：

    cd gitbook-note
    git init
    git add -A
    git commit -m"add gitbook to github"
    git remote add origin github仓库url
    git push -u origin master

3.这时候就能看到本地的Gitbook已经部署到Github了

# Gitbook与Github关联

  参考资料：https://blog.csdn.net/xingzhewanfu/article/details/80108116

1.登录Gitbook账号：https://www.gitbook.com/

2.Gitbook新建一个空间，可看到页面显示：Start with a template… Or import some content…

3.选择Or import some content…下面的Sync with Git

4.按照提示去配置和安装app就可以把Gitbook与Github关联

5.Gitbook的内容Public后，可以生成可以访问的URL