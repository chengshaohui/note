# Node.js

> Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 
> Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 
> Node.js 的包管理器 npm，是全球最大的开源库生态系统。

## nodejs能做什么

1. 在服务器上开发脚本（小程序）
2. 在程序员的电脑上  前端自动化
3. 提供web服务器

```js
//开发一些方便的脚本
const fs = require('fs'); //文件系统
const os = require('os'); // operation system
const path = require('path');
const desktop = path.join(os.homedir(), 'Desktop');
fs.mkdirSync(path.join(desktop, 'aa'));
fs.readdir(desktop, (err, files)=> {
    files.forEach(v=> {
        if (path.extname(v) === '.xlsx') {
            fs.renameSync(
                path.join(desktop, v),
                path.join(desktop, 'aa', v)
            )
        }
    })
});
// 前端自动化
const fs = require('fs'); //filesystem
fs.watchFile('./index.scss', ()=> {
    fs.createReadStream('./index.scss')
        .pipe(fs.createWriteStream('.index.css'))
});
//提供web服务
const http = require('http');
const server = http.createServer((req, res)=> {
    res.writeHead(200,{
        'Content-Type':'text/html'
    });
    res.end('<html><body><h1>this is h1</h1></body></html>');
});
server.listen(8888);
```

## 新的数据类型

### Buffer

> 表示文件最原始的存储方式（字节）（16进制代表一个字节） 又小又整齐

## module (模块)

> Node.js 有一个简单的模块加载系统。 在 Node.js 中，文件和模块是一一对应的（每个文件被视为一个独立的模块）。

### 模块化编程的好处

> 为了编写可维护的代码，我们把很多函数分组，分别放到不同的文件里，这样，每个文件包含的代码就相对较少，很多编程语言都采用这种组织代码的方式。在Node环境中，一个.js文件就称之为一个模块

* 最大的好处是大大提高了代码的可维护性
* 编写代码不必从零开始。当一个模块编写完毕，就可以被其他地方引用。
* 可以避免函数名和变量名冲突

### require函数参数（string)

1. 绝对路径
2. 相对路径
3. .js可以省略（默认找.js    .json) (如果是文件夹 默认找其下的index.js)
4. 直接写字符串(引入内置模块和node_modules文件夹下的模块)

### CommonJS规范

这种模块加载机制被称为CommonJS规范。在这个规范下，每个`.js`文件都是一个模块，它们内部各自使用的变量名和函数名都互不冲突。

### 基本模块

#### child_process

* child_process.spawnSync(command,  args)
  * 使用给定的 `command` 和 `args` 中的命令行参数来衍生一个新进程

#### fs

> Node.js内置的`fs`模块就是文件系统模块，负责读写文件。

* fs.readFile(path[, options], callback)
* fs.writeFile(file, data[, options], callback)
* fs.unlink(path, callback)
* fs.stat(path, callback)
  * fs.stat(path, callback).isFile()
  * fs.stat(path, callback).isDirectory()
  * fs.stat(path, callback).isDirectory().ctime
* fs.rename(oldPath, newPath, callback)
* fs.unlink()
* fs.mkdir(path[, mode], callback)   
  * 只能建一层
* fs.rmdir(path, callback)
* fs.readdir(path[, options], callback)
* fs.watch(filename, [,options], [,listener])
* fs.createReadStream(path[, options])
* fs.createWriteStream(path[, options])
* fs.existsSync(path)

##### 异步读文件

```js
var fs = require('fs');
fs.readFile('sample.txt', 'utf-8', function (err, data) {
    if (err) {
        console.log(err);
    } else {
        console.log(data);
    }
});
//异步读取时，传入的回调函数接收两个参数，当正常读取时，err参数为null，data参数为读取到的String。当读取发生错误时，err参数代表一个错误对象，data为undefined。这也是Node.js标准的回调函数：第一个参数代表错误信息，第二个参数代表结果。
```

##### 同步读文件

> 除了标准的异步读取模式外，`fs`也提供相应的同步读取函数。同步读取的函数和异步函数相比，多了一个`Sync`后缀，并且不接收回调函数，函数直接返回结果。

```js
var fs = require('fs');
var data = fs.readFileSync('sample.txt', 'utf-8');
console.log(data);
```

##### 写文件

> 将数据写入文件是通过`fs.writeFile()`实现的：

```js
var fs = require('fs')
var data = 'Hello, Node.js'
fs.writeFile('output.txt', data, function (err) {
    if (err) {
        console.log(err)
    } else {
        console.log('ok')
    }
})
//writeFile()的参数依次为文件名、数据和回调函数。如果传入的数据是String，默认按UTF-8编码写入文本文件，如果传入的参数是Buffer，则写入的是二进制文件。回调函数由于只关心成功与否，因此只需要一个err参数。
```

和`readFile()`类似，`writeFile()`也有一个同步方法，叫`writeFileSync()`：

```js
var fs = require('fs')
var data = 'Hello, Node.js'
fs.writeFileSync('output.txt', data)
```

##### stat

> 如果我们要获取文件大小，创建时间等信息，可以使用`fs.stat()`，它返回一个`Stat`对象，能告诉我们文件或目录的详细信息：

```js
var fs = require('fs');
fs.stat('sample.txt', function (err, stat) {
    if (err) {
        console.log(err);
    } else {
        console.log('isFile: ' + stat.isFile()); // 是否是文件
        console.log('isDirectory: ' + stat.isDirectory()); // 是否是目录
        if (stat.isFile()) {
            console.log('size: ' + stat.size); // 文件大小
            console.log('birth time: ' + stat.birthtime); // 创建时间, Date对象
            console.log('modified time: ' + stat.mtime); // 修改时间, Date对象
        }
    }
}); 
/*
isFile:true
isDirectoryfalse
size:11
birth time: Mon Nov 13 2017 22:59:41 GMT+0800 (中国标准时间)
modified time: Mon Nov 13 2017 22:59:41 GMT+0800 (中国标准时间)
*/
```

##### 异步还是同步

> 由于Node环境执行的JavaScript代码是服务器端代码，所以，绝大部分需要在服务器运行期反复执行业务逻辑的代码，**必须使用异步代码**，否则，同步代码在执行时期，服务器将停止响应，因为JavaScript只有一个执行线程。

服务器启动时如果需要读取配置文件，或者结束时需要写入到状态文件时，可以使用同步代码，因为这些代码只在启动和结束时执行一次，不影响服务器正常运行时的异步执行。

##### stream

> `stream`是Node.js提供的又一个仅在服务区端可用的模块，目的是支持“流”这种数据结构。
>
> 流是一种抽象的数据结构, 流的特点是数据是有序的，而且必须依次读取，或者依次写入，不能像Array那样随机定位。

* 有些流用来读取数据，比如从文件读取数据时，可以打开一个文件流，然后从文件流中不断地读取数据。
* 有些流用来写入数据，比如向文件写入数据时，只需要把数据不断地往文件流中写进去就可以了。

在Node.js中，流也是一个对象，我们只需要响应流的事件就可以了：

* `data`事件表示流的数据已经可以读取了
* `end`事件表示这个流已经到末尾了，没有数据可以读取了
* `error`事件表示出错了

```js
var fs = require('fs');

// 打开一个流:
var rs = fs.createReadStream('sample.txt', 'utf-8');

rs.on('data', function (chunk) {
    console.log('DATA:')
    console.log(chunk);
});

rs.on('end', function () {
    console.log('END');
});

rs.on('error', function (err) {
    console.log('ERROR: ' + err);
});
// 所有可以读取数据的流都继承自stream.Readable，所有可以写入的流都继承自stream.Writable。
```

pipe

> 就像可以把两个水管串成一个更长的水管一样，两个流也可以串起来。一个`Readable`流和一个`Writable`流串起来后，所有的数据自动从`Readable`流进入`Writable`流，这种操作叫`pipe`

在Node.js中，`Readable`流有一个`pipe()`方法，就是用来干这件事的。

用`pipe()`把一个文件流和另一个文件流串起来，这样源文件的所有数据就自动写入到目标文件里了，所以，这实际上是一个复制文件的程序：

```js
var fs = require('fs');

var rs = fs.createReadStream('sample.txt');
var ws = fs.createWriteStream('copied.txt');

rs.pipe(ws);
```

#### http

> `http`模块主要用于搭建HTTP服务

* http.createServer([requestListener])
  * http.createServer((req, res) => {})
    * req IncomingMessage 类的实例（events)  可读可写流
    * res ServerResponse 类的实例 （events)    可读可写流
* http.request(options[, callback\])

**req**

* **message**.url
  * 返回请求的 URL 字符串。 仅包含实际 HTTP 请求中的 URL

**res**

* response.end([data][, encoding][, callback])
  * 该方法会通知服务器，所有响应头和响应主体都已被发送，即服务器将其视为已完成。 每次响应都必须调用 `response.end()` 方法

```js
const http = require('http')
const fs = require('fs')
const os = require('os')
// -req IncomingMessage 类的实例（events）'aborted' 事件 'close' 事件  可读可写流
// -res ServerResponse 类的实例 （events) 'close' 事件 'finish' 事件   可读可写流
// url 是资源
const o = require('./tools.js')
let index = (req, res) => {
	let lis = ''
	let files = fs.readdirSync('./upload')
	files.forEach((file) => {
	  	lis += `<li class="list-group-item">${file}</li>`
	})
	fs.readFile('./views/index.html', (err, buffer) => {
		let b = buffer.toString().replace('{{}}', lis)
		res.end(b)
	})
}
let me = (req, res) => {
	fs.createReadStream('./img/icon.jpg').pipe(res)
}
let fn = (req, res) => {
	if (req.url == '/') {
		index(req, res)
	} else if(req.url == '/me') {
		me(req, res)
	} else if (req.url == '/upload') {
		let w = fs.createWriteStream('./upload/' + Math.random() + '.jpg')
		req.on('data', (chunk) => {
			// TODO：
			//1. 去掉开头和结尾------WebKitFormBoundaryocBhNZvx1N1l6F7M
			//2. 把文件名和文件类型都取出来
			w.write(chunk)
		})
		req.on('end', ()=> {
			res.writeHead(301, {
				'Location': '/'
			})
			res.end()
		})
		
	} else {
		res.end('error')
	}
}
// -sever Server类的实例 （events）
const server = http.createServer(fn)
const port = 3000
server.listen(port, () => {
	// o.openUrl(o.getLocalAddress(), port)
})
```



#### os

const os = require('os');

* os.homedir()
  * 以字符串的形式返回当前用户的home目录
* os.tmpdir()
  * 返回一个字符串, 表明操作系统的 默认临时文件目录
* os.freemem()
  * 以整数的形式回空闲系统内存的字节数.
* os.totalmen()
  * 以整数的形式返回所有系统内存的字节数
* os.platform()
  * 返回一个字符串, 指定Node.js编译时的操作系统平台
* os.EOL
  * 一个字符串常量,定义操作系统相关的行末标志:
* os.getNetworkInterfaces()
  * 返回一个对象,包含只有被赋予网络地址的网络接口.

#### path



const path = require('path')

* path.join([...paths])
  * 使 用平台特定的分隔符把全部给定的 `path` 片段连接到一起，并规范化生成的路径
* path.resolve([...paths])
  * 把一个路径或路径片段的序列解析为一个绝对路径
* path.basename(path[, ext])
  * 返回一个 `path` 的最后一部分，类似于 Unix 中的 `basename` 命令
* path.extname(path)
  * 返回 `path` 的扩展名，即从 `path` 的最后一部分中的最后一个 `.`（句号）字符到字符串结束
* path.parse(path)    // 字符串到某数据类型的转换
  * 返回一个对象，对象的属性表示 `path` 的元素
* path.format(pathObject)   // 从某数据类型到字符串的转换
  * 从一个对象返回一个路径字符串。 与 [`path.parse()`](http://nodejs.cn/api/path.html#path_path_parse_path) 相反
* path.sep
  * 提供了平台特定的路径片段分隔符
* path.delimiter
  * 提供平台特定的路径分隔符

### 事件循环机制（Event Loop）

* 时间相关的
* 网络请求相关的函数

被设计为异步

![Event Loop](http://image.beekka.com/blog/2014/bg2014100802.png)

### 全局变量

* __dirname  //绝对路径
* __filename   //绝对路径
* setImmediate(fn) = setTimeout(fn, 0)      
  * 把同步转化为异步
* process.argv
  * `process.argv` 属性返回一个数组，这个数组包含了启动Node.js进程时的命令行参数。第一个元素为[`process.execPath`](http://nodejs.cn/api/process.html#process_process_execpath)。第二个元素为当前执行的JS文件路径。剩余的元素为其他命令行参数

### 布隆过滤器

```js
// 10000以上
// 1. 布隆过滤器 （大批量数据去重）
// 优点内存可控
// 缺点 有几率误判（概率可控）
/* select * from news 
var dirt = {}
con.query('select * from news', (err, data) => {
    data.forEach(v => {
        dict[v.url0] = true
    })
})
*/
```

### 爬虫系统

地址队列  -  数据清洗  -  数据存储 （布隆过滤器）（hadoop）  