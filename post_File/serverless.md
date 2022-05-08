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
```


