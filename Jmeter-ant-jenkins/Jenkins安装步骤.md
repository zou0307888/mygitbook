<!--
 * @Author: Lily
 * @Date: 2021-12-14 10:38:31
 * @LastEditors: Lily
 * @LastEditTime: 2021-12-14 11:39:16
-->
# Jenkins安装步骤

1.下载jenkins：https://jenkins.io/

2.安装jenkins （已安装了jdk）

双击安装（傻瓜式）

3.安装好后，会自动打开浏览器 并打开地址：localhost:8080

4.按照提示的路径打开文件输入密码

5.选择安装插件，第一个为默认安装，第二个为手动

选择默认安装

6.安装完插件后，创建新用户

7.完成用户配置后，就完成安装了

8.配置环境变量

     JENKINS_HOME 为 C:\Program Files (x86)\Jenkins

9.启动Jenkins

浏览器中输入：http://127.0.0.1:8080/，打开jenkins，配置用户名、密码及插件,这里需要配置invoke ant插件、HTML测试报告展示的插件

（1）在Jenkins创建管理中点击Manage Plugins里面，安装 HTML Publisher Plugin和Ant In Workspace

（2）在Jenkins中系统管理-系统设置中，配置jdk 和 Ant