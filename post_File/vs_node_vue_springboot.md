# node_java_vue

```
###下载IDEA
IDEA开机不自动打开项目
File-settings界面中，选中 system settings 选项
去掉 reopen last project on startup 选项
IDEA破解 [https://plugins.zhile.io](https://link.zhihu.com/?target=https://plugins.zhile.io)；ide eval reset

###JAVA64位JDK
Java环境变量
JAVA_HOME， C:\Program Files\Java\jdk-11.0.2
Path  ：%JAVA_HOME%\bin；%JAVA_HOME%\jre\binmaven
https://maven.apache.org/download.cgi

###maven 环境变量
apache-maven-3.8.5-bin.zip
MAVEN_HOME ,C:\apache-maven-3.8.5,
PATH，%MAVEN_HOME%\bin
换源C:\apache-maven-3.8.5\conf\settings
<mirrors>
<mirror>
<id>aliyunmaven </id>
<mirrorOf>central </mirrorOf>
<name>aliyun maven </name>
<url>https://maven.aliyun.com/repository/public </url>
</mirror>
</mirrors>
复制匹配文件C:\Users\admin\.m2\settings
配置mavensettings.json或者使用系统变量默认配置

###vscode
{
    "java.jdt.ls.java.home":"C:\\Program Files\\Java\\jdk-11.0.2",
    "java.configuration.maven.userSettings":"C:\\apache-maven-3.8.5\\conf\\settings.xml",
    "maven.executable.path":"C:\\apache-maven-3.8.5\\bin\\mvn.cmd",
    "maven.terminal.useJavaHome":true,
    "maven.terminal.customEnv":[
        {
            "environmentVariable":"JAVA_HOME",
            "value":"C:\\Program Files\\Java\\jdk-11.0.2"
        }
    ],
    "extensions.autoUpdate": false,
}

###vscode插件列表
Chinese (Simplified) (简体中文) Language Pack for Visual Studio Code
Java Extension Pack
Maven for Java
Spring Boot Extension Pack

###360装位JDK(TM)11 64位，Java环境变量
JAVA_HOME， C:\Program Files\Java\jdk-11.0.2
Path  ：%JAVA_HOME%\bin；%JAVA_HOME%\jre\binmaven
https://maven.apache.org/download.cgi，
apache-maven-3.8.5-bin.zip，
maven 环境变量MAVEN_HOME ,C:\apache-maven-3.8.5,
PATH，%MAVEN_HOME%\bin
换源C:\apache-maven-3.8.5\conf\settings
  <mirrors>
  <mirror>
  <id>`aliyunmaven </id>
  <mirrorOf>central </mirrorOf>
  <name>aliyun maven </name>
  <url>https://maven.aliyun.com/repository/public </url>
  </mirror>
  </mirrors>
复制匹配文件C:\Users\admin\.m2\settings
配置mavensettings.json或者使用系统变量默认配置，
  
  {
    "java.jdt.ls.java.home":"C:\\Program Files\\Java\\jdk-11.0.2",
    "java.configuration.maven.userSettings":"C:\\apache-maven-3.8.5\\conf\\settings.xml",
    "maven.executable.path":"C:\\apache-maven-3.8.5\\bin\\mvn.cmd",
    "maven.terminal.useJavaHome":true,
    "maven.terminal.customEnv":[
        {
            "environmentVariable":"JAVA_HOME",
            "value":"C:\\Program Files\\Java\\jdk-11.0.2"
        }
    ],
    "extensions.autoUpdate": false,
}

###Vue_Npm_Yarn
npm install -g yarn --registry=https://registry.npm.taobao.org
yarn config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/
yarn config set registry http://registry.npm.taobao.org
yarn config get registry  // 查看yarn当前镜像源
vue-cli 安装依赖包
```
