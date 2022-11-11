

maven



```
#application
#数据库配置
spring.datasource.url=jdbc:mysql://127.0.0.1/test?useUnicode=true&characterEncoding=utf-8&serverTimezone=UTC&useSSL=true
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

#jpa
spring.jpa.properties.hibernate.hbm2ddl.auto=create
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5InnoDBDialect
spring.jpa.show-sql= true


```



```
#application.properties
# server config
server.port: 8081

# mysql
spring.datasource.url: jdbc:mysql://10.200.0.237:3306/umanager?useSSL=false&autoReconnect=true
spring.datasource.username: root
spring.datasource.password: caixianjie
spring.datasource.driver-class-name: com.mysql.jdbc.Driver
spring.datasource.dbcp2.validation-query: 'select 1'
spring.datasource.dbcp2.test-on-borrow: true
spring.datasource.dbcp2.test-while-idle: true
spring.datasource.dbcp2.time-between-eviction-runs-millis: 27800
spring.datasource.dbcp2.initial-size: 5
spring.datasource.dbcp2.min-idle: 5
spring.datasource.dbcp2.max-idle: 100
spring.datasource.dbcp2.max-wait-millis: 10000

# thymleaf
spring.thymeleaf.cache : false
    
# mybatis
mybatis.mapper-locations: classpath:mapper/*.xml
mybatis.configuration.map-underscore-to-camel-case: true
```



```
#elasticsearch
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-elasticsearch</artifactId>
</dependency>

#fstdfs
<dependency>
	<groupId>org.csource</groupId>
	<artifactId>fastdfs-client-java</artifactId>
	<version>1.27-SNAPSHOT</version>
</dependency>
```

```
#文件上传
#application.properties
spring.servlet.multipart.max-file-size=10MB
spring.servlet.multipart.max-request-size=10MB
server.port=8088

```

```
#热部署
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <optional>true</optional>
</dependency>
自动编码
```

```
#mysql
       	<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<scope>runtime</scope>
		</dependency>
```

```
#mybatis
<dependency>
			<groupId>com.baomidou</groupId>
			<artifactId>mybatis-plus-boot-starter</artifactId>
			<version>3.1.1</version>
		</dependency>
```

```
#h2database
<dependency>
			<groupId>com.h2database</groupId>
			<artifactId>h2</artifactId>
			<scope>runtime</scope>
		</dependency>
```

```
#rabbitmq
<groupId>com.neo</groupId>
	<artifactId>spring-boot-rabbitmq</artifactId>
	<version>1.0.0</version>
	<packaging>jar</packaging>
	<name>spring-boot-rabbitmq</name>
	<description>Demo project for Spring Boot and rabbitmq</description>
```

```
#redis
	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-redis</artifactId>
		</dependency>
#application*
		server:
  port: 8867
spring:
  redis:
    host: localhost
    port: 6379
    #password: ''
    database: 6
```



```
#pool2
<dependency>
			<groupId>org.apache.commons</groupId>
			<artifactId>commons-pool2</artifactId>
		</dependency>
```

```
#shiro
	<dependency>
			<groupId>org.apache.shiro</groupId>
			<artifactId>shiro-spring</artifactId>
			<version>1.7.0</version>
		</dependency>
```

```
#swagger
		 <dependency>
        <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger2</artifactId>
            <version>2.9.2</version>
        </dependency>

        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger-ui</artifactId>
            <version>2.9.2</version>
        </dependency>
```

```
#thymeleaf
	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-thymeleaf</artifactId>
		</dependency>
		<dependency>
			<groupId>nz.net.ultraq.thymeleaf</groupId>
			<artifactId>thymeleaf-layout-dialect</artifactId>
		</dependency>
```

```
	#jpa
	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
```

```
#fastjson   
<dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>1.2.62</version>
        </dependency>
```

```
 #mongodb
 <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-mongodb</artifactId>
        </dependency>

#application*     
#mongodb
spring.application.name=spring-boot-mongodb
spring.data.mongodb.uri=mongodb://192.168.0.75:20000/test

#mongodb
spring.application.name=spring-boot-multi-mongodb
mongodb.primary.uri=mongodb://192.168.0.75:20000
mongodb.primary.database=primary
mongodb.secondary.uri=mongodb://192.168.0.75:20000
mongodb.secondary.database=secondary

#
spring:
  data:
    mongodb:
      uri: "mongodb://localhost:27017/test"
```

```
 #mail
 <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-mail</artifactId>
        </dependency>
        
#mail application*
spring.mail.host=smtp.163.com
spring.mail.username=xxoo@xxoo.com
spring.mail.password=xxoo
spring.mail.default-encoding=UTF-8

# 项目contextPath，一般在正式发布版本中，我们不配置
server.context-path=/email
# 错误页，指定发生错误时，跳转的URL。请查看BasicErrorController源码便知
server.error.path=/error
# 服务端口
server.port=8004
# session最大超时时间(分钟)，默认为30
server.session-timeout=60
# 该服务绑定IP地址，启动服务器时如本机不是该IP地址则抛出异常启动失败，只有特殊需求的情况下才配置
# server.address=192.168.16.11

spring.mail.host=smtp.qq.com
spring.mail.username=576697722@qq.com
spring.mail.password=***********
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
spring.mail.properties.mail.smtp.starttls.required=true
```

```
  #oauth2
  <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-security</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.security.oauth.boot</groupId>
            <artifactId>spring-security-oauth2-autoconfigure</artifactId>
            <version>${spring-security.version}</version>
        </dependency>
```

```
   #consul 注册中心
   <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-consul-discovery</artifactId>
        </dependency>
        
          <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
        </dependency>
        
         <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        #ribbon
          <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-ribbon</artifactId>
        </dependency>
        #熔断
          <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-hystrix</artifactId>
        </dependency>
        
        #nacos
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
            <version>${nacos.version}</version>
        </dependency>
```

```
#rabbtimq
#application
server:
  port: 8702
spring:
  rabbitmq:
    addresses: 127.0.0.1
    username: guest
    password: guest
    port: 5672
    virtual-host: /
    listener:
      simple:
        acknowledge-mode: manual

```

```
#druid
spring:
  datasource:
    type: com.alibaba.druid.pool.DruidDataSource
    # 注意这里是自定义的配置，通过 JdbcParamConfig 来加载配置到 Spring 中
    # 然后由 DruidConfig 来配置数据源
    click:
      driverClassName: ru.yandex.clickhouse.ClickHouseDriver
      url: jdbc:clickhouse://127.0.0.1:8123/test # ip:port/database
      userName: default
      password: default # 按照自己连接的 clickhouse 数据库来
      initialSize: 10
      maxActive: 100
      minIdle: 10
      maxWait: 6000
      validationQuery: SELECT 1
#
# 配置druid数据源
druid.url=jdbc:mysql://localhost:3306/timebusker-spring?useUnicode=true&characterEncoding=utf8&autoReconnect=true&failOverReadOnly=false
druid.driver-class=com.mysql.jdbc.Driver
druid.username=root
druid.password=root
druid.initial-size=1
druid.min-idle=1
druid.max-active=20
druid.test-on-borrow=true
```

```
#jetty
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-jetty</artifactId>
        </dependency>
```

```
#log4j
	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-log4j</artifactId>
		</dependency>
		 ### 配置根Logger ###
log4j.rootLogger = info,stdout,D,E

### 输出到控制台 ###
log4j.appender.stdout = org.apache.log4j.ConsoleAppender
log4j.appender.stdout.Target = System.out
log4j.appender.stdout.layout = org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern =  %d{ABSOLUTE} %5p %20c{1}:%3L - %m%n

### 输出到日志文件 ###
log4j.appender.D = org.apache.log4j.DailyRollingFileAppender
log4j.appender.D.File = logs/log.log
log4j.appender.D.Append = true
## 输出DEBUG级别以上的日志
log4j.appender.D.Threshold = DEBUG
log4j.appender.D.layout = org.apache.log4j.PatternLayout
log4j.appender.D.layout.ConversionPattern = %-d{yyyy-MM-dd HH:mm:ss}  [ %t:%r ] - [ %p ]  %m%n

### 保存异常信息到单独文件 ###
log4j.appender.E = org.apache.log4j.DailyRollingFileAppender
## 异常日志文件名
log4j.appender.E.File = logs/error.log
## Append=false:默认值是true,即将消息增加到指定文件中，false指将消息覆盖指定的文件内容
log4j.appender.E.Append = true
## 只输出ERROR级别以上的日志
log4j.appender.E.Threshold = ERROR
log4j.appender.E.layout = org.apache.log4j.PatternLayout
log4j.appender.E.layout.ConversionPattern = %-d{yyyy-MM-dd HH:mm:ss}  [ %t:%r ] - [ %p ]  %m%n

###############################################################################################################################
## 自定义包下日志级别
## log4j.category.cn.timebusker.util=debug,Errorfile,Infofile,Debugfile
## 应用开发环境设定日志级别变量
log4j.category.cn.timebusker.util=${logging.level.cn.timebusker},Errorfile,Infofile,Debugfile

log4j.appender.Errorfile=org.apache.log4j.RollingFileAppender
log4j.appender.Errorfile.File=logs/core-error.log
## ImmediateFlush=true:默认值是true,意谓着所有的消息都会被立即输出。
log4j.appender.Errorfile.ImmediateFlush=true
## log4j.appender.Errorfile.DatePattern='.'yyyyMMdd
## MaxFileSize=100KB: 后缀可以是KB, MB 或者是 GB. 在日志文件到达该大小时，将会自动滚动，即将原来的内容移到core-error.log.1文件
log4j.appender.Errorfile.MaxFileSize=100MB
## MaxBackupIndex=100:指定可以产生的滚动文件的最大数
log4j.appender.Errorfile.MaxBackupIndex=100
## Threshold：指定日志消息的输出最低层次
log4j.appender.Errorfile.Threshold=error
log4j.appender.Errorfile.layout=org.apache.log4j.PatternLayout
log4j.appender.Errorfile.layout.ConversionPattern=%d{yyyy MM-dd HH:mm:ss,SSS} [timebusker] %5p [%t] %C.%M(%L) | %m%n

log4j.appender.Infofile=org.apache.log4j.RollingFileAppender
log4j.appender.Infofile.File=logs/core-info.log
## log4j.appender.Infofile.DatePattern='.'yyyyMMdd
log4j.appender.Infofile.MaxFileSize=100MB
log4j.appender.Infofile.MaxBackupIndex=100
log4j.appender.Infofile.Threshold=info
log4j.appender.Infofile.layout=org.apache.log4j.PatternLayout
log4j.appender.Infofile.layout.ConversionPattern=%d{yyyy MM-dd HH:mm:ss,SSS} [timebusker] %5p [%t] %C.%M(%L) | %m%n

log4j.appender.Debugfile=org.apache.log4j.RollingFileAppender
log4j.appender.Debugfile.File=logs/core-debug.log
## log4j.appender.Debugfile.DatePattern='.'yyyyMMdd
log4j.appender.Debugfile.MaxFileSize=100MB
log4j.appender.Debugfile.MaxBackupIndex=100
log4j.appender.Debugfile.Threshold=debug
log4j.appender.Debugfile.layout=org.apache.log4j.PatternLayout
log4j.appender.Debugfile.layout.ConversionPattern=%d{yyyy MM-dd HH:mm:ss,SSS} [timebusker] %5p [%t] %C.%M(%L) | %m%n

```

```
#lombok
     <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.16.16</version>
        </dependency>
```

```
#消息队列
<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-activemq</artifactId>
		</dependency>
		
<dependency>
            <groupId>org.springframework.kafka</groupId>
            <artifactId>spring-kafka</artifactId>
            <version>1.1.1.RELEASE</version>
        </dependency>
 <dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-amqp</artifactId>
		</dependency>
```

```
 #freemarker
 <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-freemarker</artifactId>
        </dependency>
        
spring.freemarker.cache=false
spring.freemarker.checkTemplateLocation=true
spring.freemarker.contentType=text/html
spring.freemarker.suffix=.html
spring.freemarker.templateEncoding=UTF-8
spring.freemarker.templateLoaderPath=classpath:/templates/views/
```

```
  #kaptcha
  <dependency>
            <groupId>com.github.axet</groupId>
            <artifactId>kaptcha</artifactId>
            <version>${kaptcha.version}</version>
        </dependency>
```

```
#websocket
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-websocket</artifactId>
        </dependency>
```

