<!--
 * @Author: Lily
 * @Date: 2021-12-06 16:03:16
 * @LastEditors: Lily
 * @LastEditTime: 2021-12-14 10:22:03
-->
# 1.Jmeter安装步骤
1.1、下载安装包（过程略过，自己找安装包，随便装在哪个目录下）

1.2、配置环境变量

      JMETER_HOME 为 jemter安装路径;
      CLASSPATH为 %JMETER_HOME%\lib;
      PATH为%JMETER_HOME%\bin;
　　  
1.3、安装验证
在命令窗口中输入jmeter -v回车，能出现jmeter版本则说明配置成功
 ![](..\image\jmeter\01.png)
 
可以直接在命令窗口输入jmeter回车后启动jmeter；也可以在点击jmeter.bat文件之间启动jmeter

# 2.安装JDK
2.1、下载安装包（我使用的是jdk1.8版本，自行下载）

2.2、配置环境变量

       JAVA_HOME 为 C:\Program Files (x86)\Java\jdk1.8.0_171 （注意：java我是默认装的C盘）
       CLASSPATH为  .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar;
       PATH为  %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;

2.3、安装验证

在命令窗口中输入java -version 回车，能出现java版本则说明配置成功




