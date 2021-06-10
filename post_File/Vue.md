Vue

---

sudo apt update

sudo apt-get update

sudo apt-get install nodejs			# 下载nodejs

sudo apt-get install npm		#下载npm,它是nodejs的包管理器（nodejs package manager）

npm install npm -g 升级npm

npm install -g npm

npm -g install npm

npm install cnpm -g 国内的npm不是很好用，使用cnpm代替npm的日常使用。升级或安装 cnpm

npm list -g 使用以下命令来查看所有全局安装的模块

cnpm install vue 安装vue

cnpm install --global vue-cli 全局安装 vue-cli

cnpm install webpack -g 使用 cnpm 安装 webpack

vue init webpack my-project 创建一个基于 webpack 模板的新项目

cd my-project

cnpm install	安装依赖

cnpm run dev	运行项目

---

nodejs

NPM

CNPM

npm install -g cnpm --registry=https://registry.npm.taobao.org

npm install --registry=https://registry.npm.taobao.org

cnpm install -g @vue/cli

vue ui

npm run serve

cnpm  install element-ui --save

npm install 安装

npm run serve 运行

npm run build 重建

router vue路由器

element-ui

cnpm insall element-ui

---

结构大纲

|-- build                            // 项目构建(webpack)相关代码
|   |-- build.js                     // 生产环境构建代码
|   |-- check-version.js             // 检查node、npm等版本
|   |-- dev-client.js                // 热重载相关
|   |-- dev-server.js                // 构建本地服务器
|   |-- utils.js                     // 构建工具相关
|   |-- webpack.base.conf.js         // webpack基础配置
|   |-- webpack.dev.conf.js          // webpack开发环境配置
|   |-- webpack.prod.conf.js         // webpack生产环境配置
|-- config                           // 项目开发环境配置
|   |-- dev.env.js                   // 开发环境变量
|   |-- index.js                     // 项目一些配置变量
|   |-- prod.env.js                  // 生产环境变量
|   |-- test.env.js                  // 测试环境变量
|-- src                              // 源码目录
|   |-- components                   // vue公共组件
|   |-- store                        // vuex的状态管理
|   |-- App.vue                      // 页面入口文件
|   |-- main.js                      // 程序入口文件，加载各种公共组件
|-- static                           // 静态文件，比如一些图片，json数据等
|   |-- data                         // 群聊分析得到的数据用于数据可视化
|-- .babelrc                         // ES6语法编译配置
|-- .editorconfig                    // 定义代码格式
|-- .gitignore                       // git上传需要忽略的文件格式
|-- README.md                        // 项目说明
|-- favicon.ico 
|-- index.html                       // 入口页面
|-- package.json                     // 项目基本信息

