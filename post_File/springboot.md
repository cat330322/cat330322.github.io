vscode-springboot
-----------------

360软件管家
下载vscode
插件Chinese (Simplified) (简体中文) Language Pack for Visual Studio Code
vscode 插件Java Extension Pack ，Maven for Java   ，Spring Boot Extension Pack
360软件管家JAVA64位JDK(TM)11 64位
Java环境变量
JAVA_HOME， C:\Program Files\Java\jdk-11.0.2
Path  ，%JAVA_HOME%\bin  ，%JAVA_HOME%\jre\bin
maven ，
https://maven.apache.org/download.cgi，
apache-maven-3.8.5-bin.zip，
maven 环境变量MAVEN_HOME ,C:\apache-maven-3.8.5,
PATH，%MAVEN_HOME%\bin

换源C:\apache-maven-3.8.5\conf\settings


`<mirrors>`
    `<mirror>`
    `<id>`aliyunmaven `</id>`
    `<mirrorOf>`central `</mirrorOf>`
    `<name>`aliyun maven `</name>`
    `<url>`https://maven.aliyun.com/repository/public `</url>`
    `</mirror>`
  `</mirrors>`


复制匹配文件C:\Users\admin\.m2\settings
配置mavensettings.json或者使用系统变量默认配置，

```
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
```
