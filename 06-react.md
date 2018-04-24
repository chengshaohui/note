# React

> React 是一个采用声明式，高效而且灵活的用来构建用户界面的框架

### 基本语法

#### reader

> `render` 返回的是对渲染内容的**描述**，`render` 返回的是一个 **React 元素**，是一种对渲染内容比较简洁的描述。大部分 React 开发者都会使用一种名为 JSX 的语法扩展来更方便地书写这种描述

在 JSX 中你可以任意使用 JavaScript 表达式，只需要用一个大括号把表达式括起来

#### props

> 父组件向子组件传递数据用`props`对象

#### state

> 在 React 组件的构造方法 `constructor` 当中，`this.state` 可以为该组件设置自身的状态数据

#### JSX

> 一种JavaScript 的语法扩展，推荐在 React 中使用 JSX 来描述用户界面。JSX 用来声明 React 当中的元素
>
>  Babel 转译器会把 JSX 转换成一个名为 `React.createElement()` 的方法调用。



### NPM

#### Package.json 属性说明

- name - 包名。
- version - 包的版本号。
- description - 包的描述。
- homepage - 包的官网 url 。
- author - 包的作者姓名。
- contributors - 包的其他贡献者姓名。
- dependencies - 依赖包列表。如果依赖包没有安装，npm 会自动将依赖包安装在 node_module 目录下。
- repository - 包代码存放的地方的类型，可以是 git 或 svn，git 可在 Github 上。
- main - main 字段指定了程序的主入口文件，require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。
- keywords - 关键字

#### package.json重要内容

- name, version
- scripts                                  //脚本
- (dev)(d|D)ependencies     //依赖项

#### npm

- npm init    

  > 帮助配置package.json

- npm install 

  > 安装所有的包及它的依赖项

- npm install name --save-dev  

  > 辅助做开发

- npm install name (-g) --save     

  > 安装 包到全局  C:\Users\16174\AppData\Roaming\npm 

- npm uninstall name --save 

  > 完全移除包及它的依赖项

- npm login 

  > 登陆（首次登陆） 

- npm publish

  > 提交

- npm run name

  > 跑脚本

- npm update

  > 更新模块

#### 如果想做成可安装到普通用户电脑的小程序

1. `#!/usr/bin/env node`添加到首行
2. package.json中添加 bin 字段

```json
"bin": {
   "xiazai" : "./index.js"
},
```

1. npm install -g xyz_hello

#### 自动保存文件

1. npm install -g nodemon
2. nodemon name.js

#### 要装的包

express

ejs

```js
// 设置模板引擎
server.engine('.html', require('ejs').__express)
server.set('view engine', 'html')
server.set('views', __dirname + '/views')

// 中间件 
server.use(express.static('./static'))
```

multer



### Babel

> 用于编写下一代JavaScript的编译器，可以将ES6代码转为ES5代码，从而在现有环境执行
>
> 这意味着，可以现在就用 ES6 编写程序，而不用担心现有环境是否支持

```js
/*
1. npm install -g babel-cli
2. npm install babel-preset-es2015
```

```json
{
	"scripts": {
		"build": "babel ./note.js --presets=es2015 --out-file ../010-server/static/js/note.js"
	},
	"dependencies": {
		"babel-preset-es2015": "^6.24.1"
	}
}
```



### webpack

> 前端构建工具，把各种各样的前端资源编译打包，最终输出js、css、img 

![webpack](C:\Users\16174\Pictures\001_study\webpack.png)



### 单页面应用

#### 介绍

> 单页面应用，每一个视图通过异步的方式加载，这导致页面初始化和使用过程中会加载越来越多的 JavaScript 代码，这给前端开发的流程和资源组织带来了巨大的挑战
>
> 前端是基于多语言、多层次的编码和组织工作，其次前端产品的交付是基于浏览器，这些资源是通过增量加载的方式运行到浏览器端，如何在开发环境组织好这些碎片化的代码和资源，并且保证他们在浏览器端快速、优雅的加载和更新，就需要一个模块化系统，这个理想中的模块化系统是前端工程师多年来一直探索的难题。
>
> 在编译的时候，要对整个代码进行静态分析，分析出各个模块的类型和它们依赖关系，然后将不同类型的模块提交给适配的加载器来处理。比如一个用 LESS 写的样式模块，可以先用 LESS 加载器将它转成一个CSS 模块，在通过 CSS 模块把他插入到页面的 `<style>` 标签中执行。Webpack 就是在这样的需求中应运而生。

#### 功能

> Babel和webpack都是把一个文件变成另一个文件

#### 用法

```json
/*
1. npm install -g webpack

2. a.js   b.js

3. webpack ./src/a.js  ./src/c.js

4. a.js + require('./b.js')

5. note.js  .js .js .js .js .router .app

6. webpack ./src/app.js  ../010-server/static/js/note.js
```



#### 实现

#### 1.用require   把所有文件链起来

#### 2.把不符合js语法的东西转化

```js
npm install vue --save
npm install style-loader --save-dev
npm install css-loader --save-dev
```

#### 3.搭建预览服务器

自动检测  保存刷新

代理真实的服务器

```json
{
	"scripts": {
		"start": "webpack-dev-server"
	},
	"dependencies": {
		"babel-preset-es2015": "^6.24.1",
		"vue": "^2.5.9"
	},
	"devDependencies": {
		"css-loader": "^0.28.7",
		"style-loader": "^0.19.0",
		"vue-loader": "^13.5.0",
		"vue-template-compiler": "^2.5.9"
	}
}
// 两个全局安装
```



###  JSX

> 一种 JavaScript 的语法扩展

```jsx
// 时间和http请求是异步

// 表达式求值符
{} 
// 检测表达式方法
1. console 就是表达式求值器
2. 断点调试工具可以直接运行表达式，进行求值
```



1. ktv  后台迁移   php => node


2. 百度云上建立一个项目   node v4.4.4  abc-ktv.duapp.com
3. 010-ktv-server 012-ktv    012-ktv  proxy:baiduyun

百度云做测试服务器

```js
//虚拟DOM
// 1. dom 2.data 3.交互 4.样式




//外部数据不可更改
//内部更改之后render函数会重新调用



history
// history.pushState || hash 更改浏览器地址但不会发起请求
// window.onpopstate   浏览器点击后退前进按钮触发
// history.state = 调用pushState函数的第一个参数
// router 放到本页面
```

### react 项目搭建过程

```json
/*   为build成功而奋斗！
1. npm i create-react-app -g     //官方提供的脚手架

2. create-react-app 014-ktv-manager

3. cd 014-ktv-manger

4. npm run eject

5. 跟进程序代码 "scripts": "node scripts/build.js"   ->  config/webpack.config.prod.js
-> config/paths    

6. paths appBuild 修改为 path.resolve(__dirname, '../../010-server/public./admin') 

7. static去掉，一共四处   webpack.config.prods.js  '' 

8. scripits/build.js  49行   fs.empryDirSync()   注释掉 否则清空public下所有文件夹

9 服务器上的回文件的代码换成   res.sendFile('./public/ad/index.html')

10. package.json中加配置  "homepage": "localhost:18080/admin"

11.	package.json中加代理配置  "proxy": "http://chengshaohuiktv.duapp.com",

npm run build 
npm i anid -s


```



### HTTP

> HTTP 是基于 TCP/IP 协议的[**应用层协议**](http://www.ruanyifeng.com/blog/2012/05/internet_protocol_suite_part_i.html)。它不涉及数据包（packet）传输，主要规定了客户端和服务器之间的通信格式，默认使用80端口。

Content-Type: text/html

​			  text/plain

​			  image/png

​			  application/json

queryString: 

Set-cookie: a= 1 





1.cookie 服务器设置， 'Set-Cookie

2 .cookie会跟随一次同域名http请求

cookie隔离技术



### React-native项目

#### 环境搭建

0.  npm i npm@4 -g


1. npm install -g create-react-native-app
2. create-react-native-app myktv
3. cd myktv
4. npm start


5. [Expo](https://expo.io/)   手机app  扫二维码   （国内app市场中找到）

-----------

5. node (-v 已有)  Python2（[Chocolatey](https://chocolatey.org/)）    @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
6. choco -v     
7. choco install  python2   
8. python  -v
9. choco install    jdk8     (java官网上也能安装jdk8)
10. java  -version

----



5. npm install -g react-native-cli
6. react-native init AwesomeProject  (用编辑器打开)
7. cd AwesomeProject



1. Install Android Studio  装上sdk  |   装上编辑器
2. Install the Android SDK    勾对（）  |   安装Android SDK（参考文档图，一个一个勾）
3. Configure the ANDROID_HOME environment variable   (配置安卓home)  |  (连上真机，用编辑器打开native, 图标里有个设备按钮； 安装虚拟设备（参考文档图）安装成功后要启动（注意HAXM错误， 出了这个错误根据指示去修改BIOS设置）)



5. 最后一步： react-native run-android (把代码发到手机或虚拟设备)




# 常遇到的问题

### WebSocket

> HTML5开始提供的一种浏览器与服务器间进行全双工通讯的网络通信协议
>
> 在WebSocket API中，浏览器和服务器只需要要做一个握手的动作，然后，浏览器和服务器之间就形成了一条快速通道。两者之间就直接可以数据互相传送

#### 为什么需要HTTP协议外的另一个协议？

因为 HTTP 协议有一个缺陷：通信只能由客户端发起，做不到服务器主动向客户端推送信息。

这种单向请求的特点，注定了如果服务器有连续的状态变化，客户端要获知就非常麻烦。只能使用["轮询"](https://www.pubnub.com/blog/2014-12-01-http-long-polling/)：每隔一段时候，就发出一个询问，了解服务器有没有新的信息。最典型的场景就是聊天室。

轮询的效率低，浪费资源（因为必须不停连接，或者 HTTP 连接始终打开）。因此，工程师们一直在思考，有没有更好的方法。WebSocket 就是这样发明的。

#### 特点

它的最大特点就是，服务器可以主动向客户端推送信息，客户端也可以主动向服务器发送信息，是真正的双向平等对话，属于[服务器推送技术](https://en.wikipedia.org/wiki/Push_technology)的一种。

其他特点包括：

（1）建立在 TCP 协议之上，服务器端的实现比较容易。

（2）与 HTTP 协议有着良好的兼容性。默认端口也是80和443，并且握手阶段采用 HTTP 协议，因此握手时不容易屏蔽，能通过各种 HTTP 代理服务器。

（3）数据格式比较轻量，性能开销小，通信高效。

（4）可以发送文本，也可以发送二进制数据。

（5）没有同源限制，客户端可以与任意服务器通信。

（6）协议标识符是`ws`（如果加密，则为`wss`），服务器网址就是 URL。



### 跨域的解决方案

1. 通过Flash插件发送HTTP请求，这种方式可以绕过浏览器的安全限制，但必须安装Flash，并且跟Flash交互。
2. 二是通过在同源域名下架设一个代理服务器来转发，JavaScript负责把请求发送到代理服务器。代理服务器再把结果返回，这样就遵守了浏览器的同源策略。
3. 第三种方式称为JSONP，它有个限制，只能用GET请求，并且要求返回JavaScript。这种方式跨域实际上是利用了浏览器允许跨域引用JavaScript资源
4. 如果浏览器支持HTML5，那么就可以一劳永逸地使用新的跨域策略：CORS（跨域资源共享）了