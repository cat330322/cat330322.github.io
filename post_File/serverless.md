### serverless
---


```
###
https://my-vue-starter-1258443814.cos-website.ap-guangzhou.myqcloud.com/#/
音乐网站:网易云https://music.163.com/
常用:
Youtube:https://www.youtube.com
腾讯云 https://cloud.tencent.com/
phh_study :https://www.xp.cn/linux.html
serverless官网:https://cn.serverless.com/
中文技术社区:https://serverlesscloud.cn/
知乎专栏https://zhuanlan.zhihu.com/ServerlessGo
Serverless:框架开发资源汇总https://github.com/yugasun/awesome-serverless-framework
SegmentFault:https://segmentfault.com/t/serverlessframework

###queryMysql.js
module.exports = {
	devServer:{
		proxy:{
			'api':{
			target:'http://localhost:5858/', 	//接口域名
			changeOrigin:true, 					//是否跨域
			ws:true,							//是否代理websockets
			secure:true,						//是否https接口
			pathRewrite:{						//路径重置
			'^/api':''
				}
			}
		}
	}
};

###app.js
/*
	用途:中间件,通过它操作mysql
*/
var express = require('express');
var app = express()
var mysql = require('mysql')

//创建连接mysql对象
var connection = mysql.createConnection({
	host:'localhost',
	user:'root',
	password:'root',
	port:'3306',
	database:'temp',
})

//第一个接口
app.get('/query',function(req,res){
	//连接
	connection.connect()
		var sql = 'select * from test_tbl'
	//查找
	connection.query(sql, function(err,result){
		console.log(result)
		res.send(result)
	});
	//关闭
		connection.end()
})
app.listen(5858,function(){
	console.log('5858,mysql,中间件已经执行')
})

###express_server.js
const express =  require ('express');
const os = require('os'); 
const app =express();

function getIpAddress() {
    var ifaces=os.networkInterfaces()
    for (var dev in ifaces) {
      let iface = ifaces[dev]
      for (let i = 0; i < iface.length; i++) {
        let {family, address, internal} = iface[i]
        if (family === 'IPv4' && address !== '127.0.0.1' && !internal) {
          return address
        }
      }
    }
  }
 let ipAddress = getIpAddress()

app.use(express.static(__dirname + '/public/dist'));

app.get('/get_username',function(request,response){
    response.send({
        name:'zhangsan'
    })
});
app.get('/ip',function(request,response){
    response.send({
    本机IP地址:ipAddress
    })
});
app.get('/get_classname',function(req,res){
    res.send({
        name:'1111班级'
    })
})

app.listen(3000,function(err){
    if(err){
        console.log(err);
        return;
    }
    console.log('服务已经启动,请访问3000')
})

###安装 Serverless Framework
# 使用 npm 全局安装 serverless 命令行工具
$ npm install -g serverless
# 使用 cnpm 及镜像全局安装 serverless 命令行工具
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
$ cnpm install -g serverless
# 升级 serverless 命令行到最新版本
$ npm update -g serverless
# 通过express-starter模版初始 Express 组件应用
$ sls init express-starter
# 通过express-starter模版初始 Express 组件应用并指定目录名称
$ sls init express-starter --name my-express-app
# 部署组件应用到到云端服务器
$ sls deploy
# 部署指定目录下的组件实例到云端服务器(适用于多组件应用)
$ sls deploy --target ./src
# 通过安装包进行安装
$ curl -o- -L https://slss.io/install | bash
# 使用 serverless 的升级命令来升级到最新版本
$ serverless upgrade
# 查看系统当前 serverless 版本信息
$ serverless -v
# 进入组件应用的开发调试模式
$ sls dev
# 调用函数应用默认函数
$ serverless invoke local
# 调用单函数应用函数并指定 Event 数据
$ serverless invoke local --data '{"foo":"bar"}'
# 调用函数应用默认函数
$ serverless invoke
# 调用函数应用默认函数的生产环境版本并使用指定 Event 数据
$ serverless invoke --stage prod --data '{"foo":"bar"}'
# 查看全部组件模板信息
$ sls registry
# 查看指定组件模板信息
$ sls registry express-starter
# 删除组件应用实例
$ sls remove
# 删除指定目录下的组件应用实例
$ sls remove --target ./src
# 查看当前组建的日志
$ serverless logs
# 启动监听模式查看当前组建的日志并每5秒刷新一次
$ serverless logs --tail --interval 5000

###Serverless 开发流程
使用 CLI 命令 sls (命令行交互) 来创建一个 serverless 官方模板应用。
使用 CLI 命令 sls init {模板名称} （指定模板） 来创建一个已发布的 serverless 模板应用。
手动添加 serverless.yml 并完成 serverless 应用配置将任意项目转化为 serverless 应用。
sls dev : 启动远程开发模式，更多调试模式详情请参考远程开发模式。
sls invoke local : (仅支持云函数开发) 本地调用函数。 同时可以发送 event 和 context 数据到函数进行本地调用测试。
sls invoke : (仅支持云函数开发) 调用已部署函数，可以发送自定义 event 数据来调用函数，在结果中可以查看日志，以及其他函数调用相关信息。
sls logs : 查看应用云端指定时间区间的日志或实时日志。

###serverless.yml 配置文件
	
# ##Serverless 应用信息##
app: my-scf-node-demo-6d53f98e # app名称(app唯一识别标识)。同账号下需唯一
component: scf # 要使用组件
name: scf-nodejs # 组件实例名称
 
# ##scf 组件配置##
inputs:
  src: ./ # 执行目录
  type: event # 函数类型（默认event）
  name: my-scf-instance-name # 实例名称(可选)
  handler: index.main_handler # 函数方法名称
  region: ap-guangzhou # 部署目标地区
  runtime: Nodejs10.15 # 运行环境
  memorySize: 128
  timeout: 3
  events: # 触发器
    - apigw: # api网关触发器
        parameters:
          endpoints:
            - path: /
              method: GET
	      
###vue.config.js
module.exports = {
  devServer:{
    proxy:{
      '/api':{
        target :'http://localhost:5858',//接口域名
        changeOrigin: true,
        ws: true,
        secure: true,
        pathRewrite:{
          '^/api':''
        }
      }
    }
  }
};
```


