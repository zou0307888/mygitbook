# Sourcetree
  参考地址：https://www.cnblogs.com/fisherbook/p/11397168.html
# 一.简介：
一个用于Windows和Mac的免费Git客户端。

Sourcetree简化了如何与Git存储库进行交互，这样您就可以集中精力编写代码。通过Sourcetree的简单Git GUI可视化和管理存储库。

官网下载地址：Sourcetree | Free Git GUI for Mac and Windows 

# 二.使用方法
1.安装

下载完成后，在安装SourceTree的过程中，需要通过账户登录，但注册或登录界面可能根本无法打开，导致软件无法正常安装。

解决方法：

(1)、在目录C:\Users\{youruser}\AppData\Local\Atlassian\SourceTree 下创建文件accounts.json ，注意：{youruser}需要替换为登录系统用户名。如我的电脑路径为：

C:\Users\Administrator\AppData\Local\Atlassian\SourceTree。写入如下内容：
   [
  {
    "$id": "1",
    "$type": "SourceTree.Api.Host.Identity.Model.IdentityAccount, SourceTree.Api.Host.Identity",
    "Authenticate": true,
    "HostInstance": {
      "$id": "2",
      "$type": "SourceTree.Host.Atlassianaccount.AtlassianAccountInstance, SourceTree.Host.AtlassianAccount",
      "Host": {
        "$id": "3",
        "$type": "SourceTree.Host.Atlassianaccount.AtlassianAccountHost, SourceTree.Host.AtlassianAccount",
        "Id": "atlassian account"
      },
      "BaseUrl": "https://id.atlassian.com/"
    },
    "Credentials": {
      "$id": "4",
      "$type": "SourceTree.Model.BasicAuthCredentials, SourceTree.Api.Account",
      "Username": "username@email.com"
    },
    "IsDefault": false
  }
]

（2）、重新启动软件，顺利进入界面。