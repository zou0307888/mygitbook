<!--
 * @Author: Lily
 * @Date: 2021-12-14 10:22:30
 * @LastEditors: Lily
 * @LastEditTime: 2021-12-14 10:35:35
-->
# 安装Ant
参考地址：https://www.cnblogs.com/wulixia/p/11011793.html

1.1 安装包下载

下载地址 http://ant.apache.org/bindownload.cgi，下载后解压到指定位置即可，我是与jmeter放在同一位置

1.2 配置环境变量

     ANT_HOME 为 ant解压位置
     CLASSPATH为 %ANT_HOME%\lib;
     PATH为%ANT_HOME%\bin;

1.3 安装验证

验证安装结果,命令行输入ant -v，出现版本信息则安装成功

2.Ant配置jmeter

用ant构建命令来调动执行jmeter接口测试，并生成测试报告  

2.1 配置库文件

将jmeter extras目录下的ant-jmeter-1.1.1.jar文件拷贝到ant安装目录下的lib文件夹中

2.2 配置ant的编译文件build.xml

新建的txt文件，并将此文件改名为build.xml，修改文档里的内容，将build.xml放置ant\bin目录下

按实际情况修改如下文档：

        <?xml version="1.0" encoding="UTF-8"?>

        <project name="ant-jmete-test" default="all" basedir=".">
        <tstamp>
        <format property="time" pattern="MM-dd-hh-mm"/>
        </tstamp>
        <!--需要改成自己本地的jmeter目录-->
        <property name="jmeter.home" value="D:\Tools\apache-jmeter-4.0"/>
        <property name="jmeter.dir" value="${jmeter.dir}"/>
        <!--jmeter生成jtl格式的结果报告路径-->
        <property name="jmeter.result.jtl.dir" value="D:\Tools\apache-jmeter-4.0\bin\test\jmeter_report\jtl"/>
        <!--jmeter生成html格式的结果报告路径-->
        <property name="jmeter.result.html.dir" value="D:\Tools\apache-jmeter-4.0\bin\test\jmeter_report\html"/>
        <!--生成报告的前缀-->
        <property name="ReportName" value="TestReport"/>
        <property name="jmeter.result.jtlName" value="${jmeter.result.jtl.dir}/${ReportName}${time}.jtl"/>
        <property name="jmeter.result.htmlName" value="${jmeter.result.html.dir}/${ReportName}${time}.html"/>
        <!--接收测试报告的邮箱-->
        <!--<property name="mail_to" value="lily@17track.cn"/>-->
        <target name="all">
        <antcall target="test"/>
        <antcall target="report"/>
        </target>
        <target name="test">
        <taskdef name="jmeter" classname="org.programmerplanet.ant.taskdefs.jmeter.JMeterTask"/>
        <jmeter jmeterhome="${jmeter.home}" resultlog="${jmeter.result.jtl.dir}/${ReportName}${time}.jtl">
        <!--声明要运行的脚本，.jmx指包含此目录下的所有jmeter脚本-->
        <testplans dir="D:\Tools\apache-jmeter-4.0\bin\test" includes="*.jmx"/>
        <property name="jmeter.save.saveservice.output_format" value="xml"/>
        </jmeter>
        </target>


        <target name="report">
        <tstamp>
        <format property="report.datestamp" pattern="yyyy/MM/dd MM:mm"/>
        </tstamp>
        <xslt classpathref="xslt.classpath" force="true" in="${jmeter.result.jtlName}" out="${jmeter.result.htmlName}" style="${jmeter.home}/extras/jmeter.results.shanhe.me.xsl">
        <param name="dateReport" expression="${report.datestamp}"/>
        </xslt>
        <!--因为上面生成报告的时候，不会将相关的图片也一起拷贝至目标目录，所以需要手动拷贝-->
        <copy todir="${jmeter.result.html.dir}">
        <fileset dir="${jmeter.home}/extras">
        <include name="collapse.png"/>
        <include name="expand.png"/>
        </fileset>
        </copy>
        </target>
        <path id="xslt.classpath">
        <fileset dir="${jmeter.home}/lib" includes="xalan*.jar"/>
        <fileset dir="${jmeter.home}/lib" includes="serializer*.jar"/>
        </path>
        </project>

2.3 配置jmeter.propertise文档

找到jmeter.properties文档，在jmeter/bin目录下，打开该文档并编辑，修改jmeter报告输出格式为xml：

改jmeter.save.saveservice.output_format=csv 为jmeter.save.saveservice.output_format=xml，并去掉前面的注释符号#

2.4 验证配置，执行构建测试

在build.xml所在目录打开命令窗口（鼠标在空白处按下shift键后在右键），

或者命令行cd到build.xml文件所在目录，输入ant run回车，执行测试

2.5 查看测试报告

在报告输出存放路径下查看是否有jtl和html结果报告，存放路径在build文档中也有

打开html文档，测试结果展现了执行的用例名称、成功率、用例执行时间等结果参数

这样的结果是不是不太直观，因为用jmeter自带的测试报告得到的测试报告信息并不是很全，下面讲一下怎么优化测试报告

2.6 优化测试报告

（1）、下载优化模板 jmeter-results-shanhe-me.xsl，拷贝到jmeter的extras目录中

（2）、设置测试输出报告要输出的内容：同样在jmeter.properties中，设置需要输出的内容为true，并去掉前面的注释符号#，这里全部设置成true→保存

（3）设置build文件的报告模板为优化后的模板jmeter-results-shanhe-me.xsl

（4）再次用ant构建测试，查看优化后的测试报告















