# **js历史**

> 是基于事件和对象驱动的解释性，松散型的语言
>
> 解释性：由浏览器解释执行
>
> 松散型：变量可以用来保存任何类型的数据

- 布兰登艾奇 
- 引入方式
  - 外链js
  - 内嵌js
  - 重定向
- 测试方式
  - alert()
  - console.log()
  - document.write()
- 组成部分
  - ECMAscript ,基础语法
  - BOM 浏览器对象模型
  - DOM 文档对象模型
- 作用
  - 写网页的动态效果
  - 写网页的游戏
  - 使用cookie、sessicon
  - 实现交互
  - 发送表单form
  - 发送ajax
  - ......

# ECMAscript

## 变量     值和址

> 就是计算机内存里的一块地址单元，为了存储数据

- 变量的定义
  - var  let  const 

```js
 var nub,nub1;
 nub=200;

 var nub=200,nub1='123';
 
 const PI=3.14;
 const arr = [1]
 arr.push('1')
```

- 命名方式
  - 可以用数字、字母、下划线、$ 构成 ,不能以数字开头
  - 不能是关键字或保留字
  - 可以用首字母大写，或驼峰命名法来命名
  - 严格区分大小写
  - 命名要有意义
- 存储         
  - 存储在栈区
  - 可以存储任何的数据类型

## 数据类型

> 根据存储位置不同来划分
>
>   基础数据类型的值一般存储在栈区              **传值**
>
>   引用数据类型的值一般存储在堆区，地址（引用） 存储在栈区               **传址**

**基础数据类型：** 

```html
Number    string    boolean      null     undefind     symbol
```

| 基础数据类型   | name  | 描述                                       |
| -------- | ----- | ---------------------------------------- |
| Number   | 数值类型  | （0B/0b十六进制  0o/0O八进制   0x/0X二进制） NaN（not a number） |
| string   | 字符串类型 | ""  ''  ``     转义序列       \n(换行符)       \f(换页符)      \t(制表符)    \r(回车符)    \b(退格)   \v(垂直制表符) |
| boolean  | 布尔类型  | true     false                           |
| null     | 空对象   | 占位符空                                     |
| undefind | 未定义   |                                          |
| symbol   |       | 表示不重复的值                                  |

**undefined**

> undefined == null  //true

- 一个变量，只声明，不赋值，默认值就是undefined
- 一个对象，没有某个属性，这个属性就是undefined
- 数组某个位置没有值，也是undefined
- 函数的参数不传值，默认传undefined
- 函数返回值，默认返回undefined


- 引用类型
  - 数组  array
  - 函数  function
  - 对象  object

```js
typeof      //number   string     boolean     object    function

instanceof    检测某一个对象是否是某一个构造函数的实例   一般用于检测引用类型    例如：//Array
```

**`` 模板字符串**

```js
var nub1 = 5
var nub2 = 40
console.log(`我们班${nub1 + nub2} 人,男生${nub2}人`)
console.log('我们班'+ (nub1 + nub2) + "人，男生" + nub2 + '人')
```



## 运算符

| 运算符   | 符号                                       | 描述                                       |
| ----- | :--------------------------------------- | ---------------------------------------- |
| 算数运算符 | +   -    *    /    %                     | \+     字符串相加表示连接，相加后变成字符串                              %    不对小数取余数                                                                                                               ++  -- 分先后 |
| 逻辑运算符 | &&     \|\|     !                        | '' 、  0 、  null、 undefined、 false、 NaN    => false |
| 比较运算符 | \>   <   >=   <=   ==   !=   ===   !==   | 字符串进行比较的时候，比较ascii码值大小                   |
| 一元运算符 | --    ++                                 |                                          |
| 三元运算符 | boolen_expression ? true_value : false-value | 根本目的：赋值；满足条件赋值                           |
| 特殊运算符 | new / delete / typeof                    | 创建对象 / 删除对象的属性 / 判断类型                    |
| 赋值运算符 | -=   +=    *=    /=    %=                |                                          |
| 扩展运算符 | ...                                      |                                          |

- 算术运算符   
  - \+     字符串相加表示连接，相加后变成字符串
  - %    不对小数取余数
  - ++  -- 分先后，+在前和在后不同，如果存在赋值的情况，+在前，先+，后赋值，反之相反。但是不论是在前还是在后，这个运算的变量结果都会+1

```js
  // Number()  不能转换undefined   // NaN
  // 调用 Number()顶层函数进行隐式转换   
  console.log(true + false)   // 1
  console.log(null + 1)  // 1
  console.log(undefined + 1) // NaN
```

- 逻辑运算符 结果不一定是boolean类型值，只要运算停留在什么位置，结果就是什么。 但是&& ,要求运算两边都得满足，|| 两边只要满足一个就行。只要这个运算能够计算出结果，立即停止运行。

```js
* &&
* ||
* !    非(!)运算结果一定是boolean类型值
```

```js
  true && 1   // 1
  true || 1   // true
  null && false // null
  1 && 2    // 2
  
  !!1   //  boolean() 函数
  

```

- 比较运算符
  - 字符串进行比较的时候，比较ascii码值大小
  - undefined==null 为真
  - ==  ===  全等需要比较类型

```js
console.log('abc' == 'acb')    // false
console.log(true > 1)   // false
console.log(true == 1)   // true
console.log(true === 1)    // false   ===  检测类型
```

- 特殊运算符 三元

  - 特殊运算符

    - new 用来创建对象
    - delete 用来删除对象的属性
    - typeof 用来检测基础数据类型  

  - 三元 （赋值——有条件的赋值）

    - var a=表达式? a:b 主要用来赋值

      ```js
      var nub = 3 ? new Array() : new Object()
      console.log(nub)     // []

      var nub = document.body.scrollTop ? document.body : document.documentElement
      ```

  - instanceof   用来检测某个对象是否是某个构造函数的实例    比如用来检测Array

  - Array.isArray(arr)

> ASCII 美国标准信息交换码       EASCII 欧洲标准     gb2312 国标   =>>  gbk（微软）（扩展【繁体字、少数民族字】）

> uncode(通用)         传输方式（utf-8）

> <u>0</u> 48       <u>a</u> 97    <u>A</u> 65       左 37   上38    右39   下40       回车13   空格32     shift16 ctrl 17   

## 表达式

> 任何有值的东西

```js
var c
1
'a'
c
var f = () => {}
f
var d = () => 5
```



## 流程控制

> 当满足某个条件的时候，按照一定顺序执行的代码

- 顺序结构

- 条件结构

  - if

  - switch 通常用来判断单个值             枚举

    ```js
    var nub = 1
    switch (nub) {
      	case 1: 
      		console.log(1)
      		console.log(1)
      		console.log(1)
      		console.log(1)
      	 break;
      	case 2:
      		console.log(2)
      		console.log(2)
      		console.log(2)
      	 break;
      	default : ;
    }              // 1 1 1 1
    ```

    ​

- 循环结构

  - for

  - while

    ```js
    var arr = []
    while(arr.length < 20) {
      arr.push(1)       //隐式的步径值
    }
    ```

  - do while 

```
   ```js
  var arr = []
  do() {
    arr.push(1)       //隐式的步径值
  } while(arr.length < 0)   // arr = [1]
```
```

​      

## 数组

> 数组就是一系列有直接或者间接联系的数据的集合
>
> 数组表示有序数据的集合，对象表示无序数据的集合。如果数据的顺序很重要，就用数组，否则就用对象。

- 声明方式

  - var arr=[];
  - var arr=new Array();

- 访问方式和设置方式

  - arr[1] 
  - arr[1]=123;
  - arr['1']
  - arr['length']
  - arr.length

- 数组遍历 

  - for 
  - foreach
  - for in 

- 二维数组

  > 一维数组的值都是数组的时候
  >
  > 循环遍历  for  for 

​```js
var arr = ['a']
console.log(arr['length'])
console.log(arr.length)

// 数据的length属性很有特点——它不是只读的。可以通过设置这个属性，从数组的末尾移除项或向数组中添加新项

//js可以使用方括号表示法来访问对象的属性。
//在使用方括号语法时，应该将要访问的属性以 【字符串的形式】 放在方括号中

//使用方括号语法的主要优点是可以通过变量来访问属性                  

两个数组链接
return [...arr1,...arr2]
```



## 函数

> 将实现某一特定功能的代码块，封装起来，以便重复使用

- **函数的定义**

  - function    // 关键字定义function的方式
  - var fun=function(){}    字面量(匿名函数赋给变量)
  - var fun=new Function(){}    不常用

- **函数的调用**   （一个函数如果不调用，那么永远也不会执行）

  - 函数名字或者是变量名字()  fun()     
  - 匿名函数的自运行  (function(){})()

- **函数的参数** 

  > 函数的参数相当于一个局部变量，可以接受任何类型的值，不论是引用数据类型还是基础数据类型

  - 形式参数和实际参数        函数在定义时候的参数，函数在运行时的参数
  - 形式参数和实际参数的个数可以不相同，如果一个形式参数没有被传参，默认传递undefined,如果一个实际参数，没有相应的形式参数接收 ，我们可以使用arguments ,会默认的接受所有传递的实际参数。
  - 函数的形式参数可以接受任何类型的数据，不论是引用类型还是基础数据类型
  - 函数的形式参数其实相当于定义的局部变量 
  - 函数的参数就是封装的接口

```js
function fun() {
  console.log(arguments[0])  //200
}
var nub1 = 200
var nub2 = 300
fun(nub1, nub2)
```

```js
function fun(nub1, nub2 = '123') {
  console.log(nub2)  //null
}
var nub1 = 200
var nub2 = 300
fun(nub1, null)

function fun(nub1, nub2 = '123') {
  console.log(nub2)  //'123'
}
var nub1 = 200
var nub2 = 300
fun(nub1, undifined)
```

- **函数的返回值**
  - 任何一个函数，在运行结束后，都会返回一个值，默认是undefined
  - 函数只能有一个返回值，但是可以有多条返回语句
  - 函数一旦返回，立即停止运行
  - fun()  这是一个表达式，表达式的值是函数的返回值
  - 函数什么时候需要返回？当我们需要用到内部的局部变量的时候，我们可以将这个变量的值返回、或者终止函数运行。

```js
var sum=function(a,b){
    var he=a+b;
    return he;
}
var num=sum(1,2); 
console.log(num)   //3
```

- **函数的作用域和作用域链**

> 作用域指变量或函数在某个范围内有意义。

> 当一个函数嵌套另外一个函数，作用域发生嵌套，就会形成作用域链 。 
> 在一个函数运行的时候，js会自动创建一个集合，用来保存可见范围内所有的变量或对象。这个集合就是作用域链。

| 作用域   | 环境     | 描述                         |
| ----- | ------ | -------------------------- |
| 全局环境  | window | 定义在全局环境中变量、函数，称为全局变量、全局函数  |
| 局部环境  | 函数     | 定义在局部环境中的变量、函数，称为局部变量、局部函数 |
| 块级作用域 |        |                            |

- **环境**
  - 宿主环境  （浏览器）
  - 运行环境 
    - 全局环境              window   全局变量
    - 局部环境              函数环境   局部变量
    - 块级作用域
- 全局变量          拥有全局的作用域  在任何位置都可以访问到         在window里面都有意义
- 局部变量          拥有局部的作用域，只能在当前环境中访问           只在当前的函数环境中有意义

```js
var nub=200;
function fun(){
    var nub=300;
    console.log();
}
fun();
console.log(nub);
```

- 预解析

> 在程序开始运行之前，js会将以var 声明的变量和以function关键字声明的函数，提前解析到相应的环境中。

> 预解析是分块解析的，但是所有的script标签对又是一个整体，已经加载的script里面的内容，可以在后面的script里面访问

```js
console.log(nub); //undefined
var nub=200;  
console.log(nub); //200
```

- **javascript 垃圾处理**

  > 找出那些不再使用的变量，然后释放其占用的内存。为此，垃圾收集器会按照固定的时间间隔（或代码执行中预定的收集时间），周期性地执行这一操作。

  - 当函数运行完毕之后，函数内部的局部变量会立即被清除
  - 当一个对象，不再被引用的时候，会在某一个时刻被删除
  - 垃圾的收集方式：

  标记清除：（常见）

  > 垃圾收集器在运行的时候会给存储在内存中的所有变量都加上标记（当然，可以使用任何标记方式）。然后，它会去掉环境中的变量以及被环境中的变量引用的变量的标记。而在此之后再被加上标记的变量将被视为准备删除的变量，原因是环境中的变量已经无法访问到这些变量了。最后，垃圾收集器完成**内存清除**工作，销毁那些带标记的值并回收它们所占用的空间

  引用计数：（不常见）

  > 跟踪记录每个值被引用的次数。当声明一个变量并将一个引用类型值赋给该变量时，则这个值的引用次数就是1。如果同一个值又被赋给另一个变量，则该值的引用次数加1。相反，如果包含这个值引用的变量又取得另外一个值，则这个值的引用次数减1。当这个值的引用次数变成0时，则说明没有办法再访问这个值了，因而就可以将其占用的内存空间回收回来。这样，当垃圾收集器下次再运行时，他就会释放那些引用次数为0的值所占用的内存

- 闭包

> 当一个函数嵌套另外一个函数，在内部函数中用到了外部函数的局部变量，在函数外部去访问内部函数的时候，就形成了闭包

```js
function aa(){
    var nub=200;
    function bb(){
         console.log(nub);
    }
    return bb;
}
var fun=aa();
  fun()  //  200 

// 按照垃圾处理，aa运行结束的时候，内部的200应该是被清除。但是这是时候，将bb函数返回，在外部调用的时候，会用到nub这个局部变量，js会将这个变量保留下来。
  
```

- **匿名函数自运行**

```js
(function () {
	alert(1);
})()
```

- **回调函数**

> 当函数的参数传递是函数的时候，这个函数就是回调函数         //当一个函数作为另一个函数参数的时候

```js
function fun(a, b, fn) {
	fn(a, b)
}
fun(1, 3, function () {
	console.log(a * b)
})      // 3
```

- **递归函数**

> 当一个函数自己调用自己的时候，就形成了递归

```js
// 阶乘  5！  n!
function jie(n) {
  if (n == 0) {
    return = 1
  }
  return n * jie(n - 1)
}

// 费波那契  1 2 3 5 8 13 ... n
function fei() {
  if (n == 1) {
    return 1
  }
  if (n == 2){
    return 2
  }
  return fei(n - 1) + fei(n - 2)
}
// 深拷贝和浅拷贝
// var arr=[[1,[]],[1,2],["a","b"]]
```

- 箭头函数

  ```js
  var arr = []
  var result = arr.map (value => value + 'new')
  ```

- 内置顶层函数

> Number()    String()    Boolean()    parseInt()    parsefloat() 

```js
// 做算术运算隐式调用Number函数
console.log(1 - true)  //0
console.log(1 - undefined)  //NaN
console.log(1 - null)   //1


// 做比较运算隐式调用Number函数
console.log(1 > true)  //false
console.log(null == undefined) //true     特殊情况
console.log(null == false) //false      特殊情况

// 做布尔运算隐式调用Boolean函数
```



## 对象

> 人们研究的一切事物都可以称之为对象

类和对象  

> 将一些具有某些特性的对象的特征抽象起来就形成类
> 类也可以作为对象 的判别，也可以用来创建对象

> 类是对象的抽象  对象是类的实例化

- 对象的创建 

  - var obj={}

    ```js
    //以json格式去创建对象
    var obj = {
        name: 'lisi',
        age: 23,
        fun: function () {
            alert(1)
        }
    }
    obj.weight = '70kg'
    var str = 'name'
    console.log(obj)
    ```

  - var obj=new 构造函数()  

    ```js
    //构造函数提供对象的初始化
    function Person(name, age) {
        this.name = name;
        this.age = age
    }
    ```

  - var obj= new Object()  

- new     发生了三件事情

```js
1.创建一个空对象  obj
2.让obj._proto_ == Person.prototype
3.Person.call(obj)
```

- 对象的属性和方法
  - 对象的一些特征，抽象之后，我们叫做属性
  - 如果这个属性的值是一个函数，我们叫做方法

```js
var obj={
    name:'lisi',
    age:123,
    fun:function(){
        
    }
}
console.log(obj.name)
console.log(obj['name'])
obj.index=1;
obj['index']=1;
obj.fun();

```

- 构造函数和普通函数区别

  - 构造函数是为了提供对象的初始化
  - 构造函数一般不用定义返回值
  - 构造函数内部会使用this
  - 都是new 构造函数

- 继承

  > js用构造函数生成实例对象,无法共享属性和方法,因此构造函数设置一个prototype属性，这个属性包含一个对象（以下简称"prototype对象"），所有实例对象需要共享的属性和方法，都放在这个对象里面；那些不需要共享的属性和方法，就放在构造函数里面
  >
  > 每个对象都有一个私有属性（称之为 [[Prototype]]），它持有一个连接到另一个称为其 prototype 对象（原型对象）的链接。该 prototype 对象又具有一个自己的原型，层层向上直到一个对象的原型为 null。（译者注：Object.getPrototypeOf(Object.prototype) === null; // true）根据定义，null 没有原型，并作为这个原型链中的最后一个环节。
  >
  > JavaScript 中几乎所有的对象都是位于原型链顶端的Object的实例。

  ​

  主要是在实例化也是new 的时候

```js
1.创建一个空对象  obj
2.让obj._proto_ == Person.prototype
3.Person.call(obj)

var obj=new person();
 person.prototype={
     aa:function(){
     }
 }
 每个对象都有__proto__ 属性    每个函数都有prototype属性   
```

- 对象的分类

  - 宿主对象  
  - 内置对象

- call()和apply()

  每个函数都有call()和apply()方法

- this

  > 谁调用this就指向谁

## 数组方法

> pop,push,reverse,shift,sort,splice,unshift 会改变原数组
>
> join,concat,indexOf,lastIndexOf,slice,toString 不会改变原数组
>
> map,filter,some,every,reduce,forEach这些迭代方法不会改变原数组

| 数组方法                    | 作用                                       | 例                                        |
| ----------------------- | ---------------------------------------- | ---------------------------------------- |
| push()*                 | 在数组后端添加任意个项并返回新数组的长度                     | var arr = [1,4,3]                                   result = arr.push('a', 'b')                              console.log(arr, result)                     // [1, 4, 3, "a", "b"]      5 |
| pop()*                  | 移除数组中最后一项并返回该项                           | var arr = [1,4,3]                                  result = arr.pop()                                          console.log(arr, result)                     // [1, 4]      3 |
| shift()*                | 移除数组中第一个项并返回该项                           | var arr = [1,4,3]                                  result = arr.shift()                                          console.log(arr, result)                     // [ 4, 3]      1 |
| unshift()*              | 在数组前端添加任意个项并返回新数组的长度                     | var arr = [1,4,3]                                 result = arr.unshift('a', 'b')                            console.log(arr, result)                    // ["a", "b", 1, 4, 3]      5 |
|                         |                                          |                                          |
| join()                  | 只接受一个参数，即用作分隔符的字符串，然后返回包含所有数组项的字符串（默认，连接） | var arr = [1,4,3]                                 result = arr.join('&')  \|\| arr.join('')            console.log(arr, result)                     // [1, 4, 3]        "1&4&3" \|\| "143" |
|                         |                                          |                                          |
| concat()                | 先创建当前数组的一个副本，然后将接收到的参数添加到副本末尾，最后返回新构建的数组 | var arr = [1,4,3]                                result = arr.concat('a', 'b')                                      console.log(arr, result)                    // [1, 4, 3]         \[1, 4, 3, "a", "b"] |
|                         |                                          |                                          |
| splice()*               | 从数组中删除、添加项目，然后返回被删除的项目arr.splice(index,num,item1,..,itemX) | var arr = [1,4,3]                               result = arr.splice(1,1,'a','b')                         console.log(arr, result)                  // [1, "a", "b", 3]       \[4] |
| slice()                 | 从已有的数组中返回选定的元素。接受一个或两个参数，即要起始位置和结束位置，不影响原数组 arr.slice(index1,index2) | var arr = [1,4,3]                               result = arr.slice(0,2)                                    console.log(arr, result)                  // [1, 4, 3]                \[1, 4] |
|                         |                                          |                                          |
| sort()*                 | 按升序排列数组项                                 | var arr = [1,4,3]                              result = arr.sort()                                          console.log(arr, result)                 // [1, 3, 4]                \[1, 3, 4] |
| reverse()*              | 反转数组项的顺序                                 | var arr = [1,4,3]                              result = arr.reverse()                                     console.log(arr, result)                 // [3, 4, 1]              \[3, 4, 1] |
| includes()              | 判断一个数组是否包含一个指定的值，如果是，酌情返回true或false      | var arr = [1,4,3]                              result = arr.includes(1)                                                        console.log(arr, result)                 // [1, 4, 3]                true |
|                         |                                          |                                          |
| **find() findeIndex()** | **filter()          forEach()          map()** | **every()                  some()**      |
| undefined   -1          | []                 undefined       [undefined] | false/true             true/false        |
| find()                  | 返回数组中满足提供测试函数的第一个元素的值。否则返回undefined      | var arr = [1,3,5,7,8]                   var result = arr.find(value => value > 5)     console.log(arr, result)             // [1, 3, 5, 7, 8]    7 |
| findIndex()             | 返回数组中满足提供测试函数的第一个元素的索引。否则返回-1            | var arr = [1,3,5,7,8]              var result = arr.findIndex(value => value > 6)     console.log(arr, result)             // [1, 3, 5, 7, 8]     3 |
|                         |                                          |                                          |
| filter()                | 对数组中的每一项运行给定函数，返回该函数会返回true的项组成的数组       | var arr = [1,3,5,7,8]                   var result = arr.filter(value => value > 4)            console.log(arr, result)             // [1, 3, 5, 7, 8]    \[ 5 , 7, 8] |
| forEach()               | 对数组中的每一项运行给定函数，这个方法没有返回值     主要用来遍历数组    | var arr = [1,3,5,7,8]                    var result = arr.forEach(value => value)                console.log(arr, result)             // [1, 3, 5, 7, 8]     undefined |
| map()                   | //映射 返回什么样的值，形成什么样的集合                    | var arr = [1,3,5,7,8]                     var result = arr.map(value => value*2)              console.log(arr, result)              // [1, 3, 5, 7, 8]    \[2, 6, 10, 14, 16] |
|                         |                                          |                                          |
| some()                  | 对数组中的每一项运行给定函数，如果该函数对任一项返回true，则返回true   | var arr = [1,3,5,7,8]                    var result = arr.some(value => value > 7)          console.log(arr, result)                // [1, 3, 5, 7, 8] true |
| every()                 | 对数组中的每一项运行给定函数，如果该函数对每一项都返回true，则返回true  | var arr = [1,3,5,7,8]                    var result = arr.every(value => value > 3)    console.log(arr, result)               // [1, 3, 5, 7, 8]  false |

## 字符串方法

| 字符串方法          | 描述                                       | 例子                                       |
| -------------- | ---------------------------------------- | ---------------------------------------- |
| charAt()       | 以单字符字符串的形式返回给指定位置的那个字符                   | var str = 'hello world'       var result = str.charAt(1)  //e |
| charCodeAt()   | 返回给指定位置的那个字符的字符编码                        | var str = 'hello world'    var result = str.charCodeAt(1)  //101 |
| fromCharCode() | 接收一个或多个字符编码，然后将它们转化成一个字符串                | var result = String.fromCharCode(104, 101, 108, 108, 111)           console.log(result)   //hello |
|                |                                          |                                          |
| concat()       | 用于将一个或多个字符串拼接起来，返回拼接的到的新字符串，不改变原先的字符串的值   可以接受任意多的参数 | var str = 'hello '    var result = str.concat('world'，’！‘)                          console.log(str, result)    //hello  hello world! |
|                |                                          |                                          |
| replace()      | 接受两个参数，第一个参数可以是RegExp对象或者一个字符串，第二个参数可以是一个字符串或者一个函数。如果第一个参数是字符串，那么只会替换第一个子字符串 | var arr = 'hello world'    var brr = arr.replace('he','ll')                                         console.log(arr, brr) //llllo world |
| split()        | 这个方法可以基于指定的分隔符将一个字符串分割成多个字符串，并将结果放在一个数组中 | var str = 'red, blue, green'                                                                                        var result = str.split(',', 2)                                                                                console.log(str, result)     //red, blue, green ["red", " blue"] |
| substr()       | 返回一个字符串中从指定位置开始到指定字符数的字符                 | var str = "abcdefghij";                                                                                              console.log("(1,2): "    + str.substr(1,2));          // (1,2): bc                                       console.log("(1): "      + str.substr(1));     // (1): bcdefghij |
| substring()    | 返回一个字符串在开始索引到结束索引之间的一个子集, 或从开始索引直到字符串的末尾的一个子集 | var anyString = "Mozilla";                                                                                        console.log(anyString.substring(0,3));     console.log(anyString.substring(3,0));     // 输出 "Moz" |
|                |                                          |                                          |
| indexOf()      | 从一个字符串中开头向后搜索给定的子字符串，然后返回子字符串的位置（如果没有找到该子字符串，则返回-1）可接受第二个参数，表示从字符串的哪个位置开始向后搜索 | var str = 'hello '    var result = str.indexOf('e')             console.log(str, result)   //    hello  1 |
| lastIndexOf()  | 从一个字符串中末尾向前搜索给定的子字符串，然后返回子字符串的位置（如果没有找到该子字符串，则返回-1）可接受第二个参数，表示从字符串的哪个位置开始向前搜索 | var str = 'helloe '    var result = str.lastIndexOf('e')        console.log(str, result)     //helloe  5 |
|                |                                          |                                          |
| slice()        | 提取字符串的一部分，并返回一新的字符串                      | var str1 = 'The morning is upon us.';                                                                      var str2 = str1.slice(4, -2);                                                                                        console.log(str2);       //   morning is upon u |
|                |                                          |                                          |
| startsWith()   | 用来判断当前字符串是否是以另外一个给定的子字符串“开头”的，根据判断结果返回 true 或 false。 | var str = "To be, or not to be, that is the question.";                                            alert(str.startsWith("To be"));         // true                                                              alert(str.startsWith("not to be"));     // false                                                           alert(str.startsWith("not to be", 10)); // true |
| endsWith()     | 用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false | var str = "To be, or not to be, that is the question.";                                        alert( str.endsWith("question.") );  // true                                                             alert( str.endsWith("to be") );      // false                                                        alert( str.endsWith("to be", 19) );  // true                                                            alert( str.endsWith("To be", 5) );   // true |
| includes()     | includes() 方法用于判断一个字符串是否包含在另一个字符串中，根据情况返回true或false | var str = 'To be, or not to be, that is the question.';                                               console.log(str.includes('To be'));       // true                                                         console.log(str.includes('To be', 1));    // false |
|                |                                          |                                          |
|                |                                          |                                          |
| toLowerCase()  | 字符串转化为小写                                 | var str = 'Hello  '            var result = str.toLowerCase()                                console.log(str, result)     //Hello   hello |
| toUpperCase()  | 字符串转化为大写                                 | var str='Hello  '              var result = str.toUpperCase()                   console.log(str, result)     //Hello   HELLO |
|                |                                          |                                          |
| trim           | 创建一个字符串的副本，删除前置及后缀的所有空格，然后返回结果           | var str = 'hello  '       var result = str.trim()    console.log(str, result)   //hello   hello |
| trimLeft       | 从一个字符串的左端移除空白字符。                         |                                          |
| trimRight      | 从一个字符串的右端移除空白字符                          |                                          |

## Math方法

| Math方法               | 描述                                   | 例子                                       |
| -------------------- | ------------------------------------ | ---------------------------------------- |
| Math.abs(num)        | 返回num的绝对值  只处理第一个参数                  | var result = Math.abs(-1)    // 1        |
| Math.max()           | 确定一组数值中的最大值，可以接受任意多的数值参数             | var result = Math.min(-1,3,2)  //-1      |
| Math.min()           | 确定一组数值中的最小值，可以接受任意多的数值参数             | var result = Math.min(-1,3,2)  //3       |
|                      |                                      |                                          |
| Math.ceil()          | 执行向上舍入，即它总是将数值向上舍入为最接近的整数   只处理第一个参数 | var result = Math.ceil(3.4)   //4        |
| Math.floor()         | 执行向下舍入，即它总是将数值向下舍入为最接近的整数  只处理第一个参数  | var result = Math.floor(3.6)   //3       |
| Math.round()         | 执行标准舍入，即它总是将数值四舍五入为最接近的整数   只处理第一个参数 | var result = Math.round(3.5)  //4        |
|                      |                                      |                                          |
| Math.random()        | 返回大于0小于1的一个随机数   不加参数   有参数没用        | var result = Math.random()   //0.5254465176488599 |
|                      |                                      |                                          |
| Math.sin(x)          | 返回x的正弦值                              | var result = Math.sin(1)     //0.8414709848078965 |
| Math.cos(x)          | 返回x的余弦值                              | var result = Math.cos(1)     0.5403023058681398 |
| Math.tan(x)          | 返回x的正切值                              | var result = Math.tan(1)        1.5574077246549023 |
|                      |                                      |                                          |
| Math.PI              | π的值                                  | var result = Math.PI     //3.141592653589793 |
| Math.pow(num, power) | 返回num的power次幂                        | var result = Math.pow(2,4)   //16        |
| Math.sqrt(num)       | 返回num的平方根                            | var result = Math.sqrt(4)   //2          |

## Date对象

> 1970年 1月 1日 0时 0分 0秒  0     元时间

**Getter**

- getFullYear()  

  > 根据本地时间返回指定日期对象的年份（四位数年份时返回四位数字）

- getMonth()    

  > 根据本地时间返回指定日期对象的月份（0-11）

- getDate()

  > 根据本地时间返回指定日期对象的月份中的第几天（1-31）

- getDay()

  > 根据本地时间返回指定日期对象的星期中的第几天（0-6）

- getHours()

  > 根据本地时间返回指定日期对象的小时（0-23）

- getMinutes()

  > 根据本地时间返回指定日期对象的分钟（0-59）

- getSeconds()

  > 根据本地时间返回指定日期对象的秒数（0-59）

- getMilliseconds()

  > 根据本地时间返回指定日期对象的微秒（0-999）

**Setter**

- setFullYear()

  > 根据本地时间为指定日期对象设置完整年份（四位数年份是四个数字）

- setMonth()

  > 根据本地时间为指定日期对象设置月份

- setDate()

  > 根据本地时间为指定的日期对象设置月份中的第几天

- setHours()

  > 根据本地时间为指定日期对象设置小时数

- setMinutes()

  > 根据本地时间为指定日期对象设置分钟数

- setSeconds()

  > 根据本地时间为指定日期对象设置秒数

## 正则RegExp()

> 正则是用来检测某个字符串是否符合语法规范的语言

应用于：    表单验证   信息过滤   信息检索

创建：

```js
var reg = /a/g         /*    /不能有数字/
/ /: 定界符   
中间: 语法规范
g: 模式修正符，代表全局匹配，改变了lastIndex属性，检索位置改变
```

**test()**

```js
let r = /png/
let str = '.png'
console.log(r.test(str))  //true
```

**exec()**

```js
let r = /png/
let str = 'aa.png'
console.log(r.exec(str)) 
//["png", index: 3, input: "aa.png"]  [代表匹配到的字符, 匹配到的字符的索引位置,检测的字符串]
```

**匹配规则**

基本概念

* 模式修正符

  > g: 全局匹配      i: 不区分大小写     m: 多行匹配


* 原子

  > 构成正则表达式最小的单位我们称之为原子

* 原子表

  > 自定义原子

* ​

```js
/*
\d: 用来匹配0-9的数字
\w: 用来匹配数字字母下划线 0-9 a-z A-Z _
\s: 用来匹配空白字符   空格   \n   \r   \t   \v   \f(换页) 
. : 用来匹配换行之外的字符
\D: 取\d补集
\W: 取\w补集
\S: 取\s补集

/*
[1-4]

/*边界匹配
^  $

```

和正则能够配合使用的字符串函数

- split()
- replace()

* match()
* search()



# BOM

## window属性和方法

- window.screen.width       // 屏幕宽度
- window.screen.height     // 屏幕高度
- alert()
- prompt()
- top
- 时间函数
  - setInterval
  - clearInterval()
  - setTimeout
  - clearTimeout()

## location

- protocol
- hostname
- port
- search
- hash
- pathname 

```js
http: / https:(http加强版，比较安全)
//超文本传输协议

// 协议    主机名+端口号/主机名   端口号   路径 查询字符串  锚地址
location.protocol     location.host/location.hostname      location.port       location.pathname location.search   location.hash
```

- location.href    

  ```js
  location.href = ("http://baidu.com") //跳转到某个页面
  ```

- location.reload(true)   

  ```js
  location.reload(true)  //重新加载 所有数据
  ```

- location.assign()    

  ```js
  location.assign('http://baidu.com') //跳转到某个页面
  ```

- location.replace() 

  ```js
  location.replace('http://baidu.com')  //不会留下历史记录
  ```

## history

- length    
- back()              // 上一个页面
- forword()       //下一个页面
- go(n)              // go(0) 刷新

```js
http: 
https：(http加强版，比较安全)
超文本传输协议
网络传输协议

TCP/IP     7层协议      网络层    
www.aebabs.com：80（端口号）(path) index.html?查询     域名   主机地址
```

## 本地存储方式

> cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。

> cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。

> sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

存储大小：

```
cookie数据大小不能超过4k。
sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。

```

有期时间：

```
localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
sessionStorage  数据在当前浏览器窗口关闭后自动删除。
cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭

```

### cookie(字符串)

> 键值对的结构   
>
> 同域原则  不能跨浏览器访问
>
> 允许存储的大小是4k;
>
> ```
> 最小的单位bit位，1位是2个状态，1Byte(字节)=8bit 1K=1024B,1M=1024KB,1G=1024MB,1T=1024G。
>
> ```

```js
function setCookie(name, value, time) {
    if (time) {
        var now = new Date();
        now.setTime(now.getTime() + time*1000);
        document.cookie = name + '=' + value+ '; expires = ' + now.toGMTString();
    } else {
        document.cookie = name + '=' + value;
    }
}
function delCookie(key) {
    var now = new Date()
    now.setTime(now.getTime()-1)
    document.cookie = key + '=' + '' + '; expires = ' + now.toGMTString()
}
function getCookie(key) {
    var cookies = document.cookie
    var arr = cookies.split('; ')
    var val
    arr.forEach(function (value, index) {
        var brr = value.split('=')
        if (brr[0] == key) {
            val = brr[1]
            return
        }
    })
    return val
}
```



### localStorage、sessionStorage

> h5新增的两种存储方式（都不安全）,只能存储字符串
>
> 存储5-10M的大小，也是同域原则，不能跨浏览器，和时间没有关系
>
> 1.localStorage（永久存储）
>
> 2.sessionStorage（会话级存储，窗口关闭删除）

```js
localStorage.name='lisi';  console.log(localStorage)  //Storage {name: "list", length: 1}
delete localStorage.name;  console.log(localStorage)  //Storage {length: 0}   
localStorage.setItem('age', '13')   console.log(localStorage.getItem('age'))  //13
localStorage.removeItem('age')   console.log(localStorage.getItem('age')) //null
// 数组和对象的存储
localStorage.arr = JSON.stringify([1, 2])
console.log(JSON.parse(localStorage.arr)) // [1,2]
localStorage.arr = JSON.stringify({a: 1, b: 2})
console.log(JSON.parse(localStorage.arr)) // {a: 1, b: 2}
```



# DOM

## 文档操作

### 获取设置文档信息

- document.url
- document.title

### 获取宽高

> 如果一个块元素如果不设置宽度，默认宽度是它父元素的宽度，默认高度是它内容的高度

- window.screen.width        //屏幕宽度

- window.screen.height      //屏幕高度

- document.documentElement.clientWidth  //获取浏览器窗口宽度

- document.documentElement.clientHeight //获取浏览器窗口高度

- ele.offsetWidth   

- ele.offsetHeight      

  > 实际宽高       不包括margin 

- ele.offsetLeft  

- ele.offsetTop

  > 计算的是距离有定位属性的上级元素的距离，如果没有定位属性的父元素，计算的是距离body的值

- document.body.scrollTop || document.documentElement.scrollTop   (没单位)

### 获取元素

- document.getElementById()
- obj.getElementsByClassName()
- obj.getElementsByTagName()
- document.getElementsByName()
- obj.querySelector()    
- obj.querySelectorAll()

### 对于元素内容的操作

- innerHTML
- innerText

### 对于元素属性的操作

#### 获取属性

- 标准属性  obj.src
- getAttribute()

#### 设置属性

- setAttribute(key, value)


- 非标准  get  set 
- class   obj.className
- class   obj.classList.add  .remove .toggle

#### 删除属性

- removeAttribute(key)

### 对于元素的样式操作

- 获取 
  - getComputedStyle(obj,null).属性  /  obj.currentStyle.样式   IE
  - 行内样式   obj.style.属性
- 添加
  - obj.style.css属性
  - obj.style.cssText
- 通过类名或者是id名，属性名字进行设置 

## 文档节点

> html文档中，所有的构成部分都是节点，每一个节点和节点之间的关系构成了整个html文档树模型

| 文档中的全部节点 | 类型       | nodeName             | nodeType | nodeValue |
| -------- | -------- | -------------------- | -------- | --------- |
| 文档节点     | document | \#document           | 9        | null      |
| 文本节点     | 文本       | \#text               | 3        | 文本内容      |
| 元素节点     | 标签       | 'DIV'    //('大写标签名') | 1        | null      |
| 注释节点     | 注释       | \#comment            | 8        | 注释内容      |
| 属性节点     | 属性       | 属性名                  | 2        | 属性值       |

### 节点的操作

#### 节点的创建

- document.createElement(nodename)

#### 节点的增加

- par.appendChild(newEle)
- par.insertBefore(newEle, oldEle)

#### 节点的删除

- par.removeChild(son)

#### 节点的复制

- obj.cloneNode(true)    //true决定子元素是否被克隆

#### 节点的替代

- par.replaceChild(newEle, oldEle)

### 获取节点

#### 获取父元素

- son.parentNode   //获取父节点
- son.parentElement  //获取父节点

#### 获取父辈的子元素

- childNodes;  //获取所有的节点组成的集合
- div.children;  //获取所有元素节点组成的集合
- par.firstChild; //获取第一个节点
- par.lastChild; //获取最后一个节点
- par.firstElementChild; //获取第一个元素节点
- par.lastElementChild; //获取最后一个元素节点

#### 获取同辈的相近元素

- sib.previousSibling;  //前一个节点
- sib.previousElementSibling;  //前一个元素节点
- sib.nextSibling;   //下一个节点
- sib.nextElementSibling;  //下一个元素节点
- insertAfter(newobj,oldobj)

```js
function insertAfter(newobj,oldobj){
    var next=oldobj.nextSibling;
    if(next){
        oldobj.parentNode.insertBefore(newobj,next)
    }else{
        oldobj.parentNode.appendChild(newobj);
    }
}
```

## 事件

> 事件是视图层到逻辑层的通讯方式,可以将用户的行为反馈到逻辑层进行处理

- 事件源
  - 事件发生在谁的身上，谁就是事件源
- 事件类型
  - 用户的行为
- 事件处理程序
  - 事件发生之后的响应
- 事件对象(e)
  - 事件发生时，自动创建的一个对象，用来保存事件发生时所有的信息

### 事件处理程序的方式

- HTML事件处理程序

  ```html
  <input type="button" onclick="alert(1)" value="click me">
  <input type="button" onclick="mess()" value="click me">
  ```

  ```js
  function mess() {
    alert(1)
  }
  ```

  缺点：

  - 存在时差问题，和script位置有关
  - html与javascript代码紧密耦合

- DOM0级事件处理程序

  ```js
  let btn = document.querySelector('#btn')
  btn.onclick = function () {
    alert(this.id)
  }
  ```

  删除：

  ```js
  btn.onclick = null
  ```

- DOM2级事件处理程序

  - addEventListener( type: DOMString, callback: EventListener, capture?: boolean )
    - 要处理的事件名
    - 作为事件处理程序的函数
    - 布尔值（false） false: 表示在冒泡阶段调用事件处理函数 true: 表示在捕获阶段调用事件处理函数
  - removeEventListener( type: DOMString, callback: EventListener, capture?: boolean )

  ```js
  function handle(e) {
      console.log(e)
  }
  let btn = document.querySelector('#btn')
  btn.addEventListener('click', handle)
  btn.removeEventListener('click', handle)
  ```

  优点：

  - 可以添加多个事件处理程序

  ```js
  function handle(e) {
      alert(1)
  }
  let btn = document.querySelector('#btn')
  btn.addEventListener('click', handle)
  btn.addEventListener('click', function () {
      alert(this.id)
  }) //同时添加两个click事件
  ```

- IE事件处理程序

  - attachEvent( type: DOMString, callback: EventListener )
  - detachEvent( type: DOMString, callback: EventListener )

  ```js
  btn.attachEvent('onclick', handle)
  btn.detachEvent('onclick', handle)
  ```

- 跨浏览器的事件处理程序

### 事件对象(e)

- clientX/Y   //  鼠标点击距离窗口的距离
- offsetX/Y   //  鼠标点击距离事件源的距离
- pageX/Y   //   body
- screenX/Y  //  屏幕

### 事件冒泡

#### 事件流

> 定义： 当一个事件触发的时候，当前元素的父元素乃至整个页面都会以一定的顺序来响应事件，响应的顺序叫做事件流

> “DOM2级事件“规定的事件流包括三个阶段：事件捕获阶段、处于目标阶段和事件冒泡阶段

#### 事件分为冒泡事件和非冒泡事件：

- 冒泡型事件流 （IE)

  > 当一个元素上的事件被触发后，该事件会向父元素传递直至根元素。

- 捕获型事件流  (IE低版本没有)

  > 从根元素开始向当前元素进行触发

- mouseenter   mouseleave 事件没有事件冒泡

- 阻止事件流 

  - e.stopPropagation() || e.returnValue = false [万恶的IE]

- 阻止特定事件的默认行为

  - preventDefault()

```js
var par = document.querySelector('.par')
    var son = document.querySelector('.son')
    var body = document.querySelector('body')
    var html = document.querySelector('html')
    par.onclick = function () {
        console.log(1)
    }

    html.addEventListener('click', function () {
        console.log('html捕获')
    }, true)
    body.addEventListener('click', function () {
        console.log('body捕获')
    }, true)
    par.addEventListener('click', function () {
        console.log('par捕获')
    }, true)
    son.addEventListener('click', function () {
        console.log('son捕获')
    }, true)
    html.onclick = function () {
        console.log('html冒泡')
    }
    body.onclick = function () {
        console.log('body冒泡')
    }
    par.onclick = function () {
        console.log('par冒泡')
    }
    son.onclick = function (e) {
        // 阻止事件流
        if (e.stopPropagation) {
            e.stopPropagation()
            e.preventDefault()
        } else {
            e.cancelBubble = true;
            e.returnValue = false
        }
        console.log('son冒泡')
}
    //html捕获  body捕获   par捕获   son捕获  son冒泡
```



### 事件委托

> 利用事件冒泡，对以下几种情况进行处理

1. 新添加进来的元素，需要事件的时候
2. 做事件优化的时候
3. 使用ajax的时候

### 事件类型

#### 鼠标事件

- click  点击
- dblclick 双击
- mousemove 鼠标移动
- mousedown 鼠标按下
- mouseup 鼠标松开
- mouseover 鼠标移入
- mouseout  鼠标移开
- mouseenter 鼠标移入
- mouseleave  鼠标离开

#### 键盘事件

- keydown   // 按下
- keypress  //按住
- keyup //松开

> <u>0</u> 48       <u>a</u> 97    <u>A</u> 65       左 37   上38    右39   下40       回车13   空格32     shift16  ctrl 17   
>
> e.ctrlKey  e.shiftKey  e.altKey          //验证alt shift ctrl有没有被按下  不能单独用

#### 表单事件

- blur  //失去焦点
- focus //获得焦点
- submit //确认按钮被点击
- reset  //重置按钮被点击
- change  //域的内容被改变

# ES6

## 类

> ES6 提供了更接近传统语言的写法，引入了 Class（类）这个概念，作为对象的模板。通过`class`关键字，可以定义类
>
> 基本上，ES6 的`class`可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的`class`写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已

构造函数：

```js
function Point(x, y) {
  this.x = x
  this.y = y
}
Point.prototype.toString = function () {
  return '(' + this.x + ', ' + this.y + ')'
}
let p = new Point(1, 2)
console.log(p, p.toString())     // {x: 1, y: 2} "(1, 2)"
```

类：

```js
class Point {
  constructor(x, y) {
    this.x = x
    this.y = y
  }
  toString() {
    return '(' + this.x + ', ' + this.y + ')'
  }
}
let p = new Point(1, 2)
console.log(p, p.toString())     // {x: 1, y: 2} "(1, 2)"
```



# Ajax

> Web的运作原理：一次HTTP请求对应一个页面。
>
> 如果要让用户留在当前页面中，同时发出新的HTTP请求，就必须用ajax发送这个新请求，接收到数据后，再用JavaScript更新页面，这样一来，用户就感觉自己仍然停留在当前页面，但是数据却可以不断地更新。

html: 超文本标记语言

xhtml: 过渡 版本

xml: 可扩展标记语言

```xml
<clothes>
  <color>red</color>
</clothes>
```





# 版本控制工具

svn：集中式管理工具          

git：分布式管理工具

在编辑器中创建.gitignore

写入：/node_modules

git clone

git pull  (多人协作)

将修改提交到暂存区

git add */name

将暂存区的文件更新到本地的仓库

git commit -m  '更新说明'

将本地仓库和网络仓库进行合并同步

git push

# json

> JSON 格式（JavaScript Object Notation 的缩写）是一种一种简便的数据交换格式，能够在服务器之间交换数据，目的是取代繁琐笨重的 XML 格式。

### JSON 对值的类型和格式有严格的规定。

- 复合类型的值只能是数组或对象，不能是函数、正则表达式对象、日期对象。
- 简单类型的值只有四种：字符串、数值（必须以十进制表示）、布尔值和`null`
- 字符串必须使用双引号表示，不能使用单引号。
- 对象的键名必须放在双引号里面。
- 数组或对象最后一个成员的后面，不能加逗号。

### **从结构上看，所有的数据最终都可以分解成三种类型**：

> 第一种类型是**标量**（scalar），也就是一个单独的字符串（string）或数字（numbers），比如"北京"这个单独的词。
>
> 第二种类型是**序列**（sequence），也就是若干个相关的数据按照一定顺序并列在一起，又叫做数组（array）或列表（List），比如"北京，上海"。
>
> 第三种类型是**映射**（mapping），也就是一个名/值对（Name/value），即数据有一个名称，还有一个与之相对应的值，这又称作散列（hash）或字典（dictionary），比如"首都：北京"。

### `JSON`对象

ES5 新增了`JSON`对象，用来处理 JSON 格式数据。它有两个方法：`JSON.stringify()`和`JSON.parse()`。

#### JSON.stringify()方法

> 该方法用于将一个值转为字符串。该字符串符合 JSON 格式，并且可以被`JSON.parse`方法还原

- 第二个参数

`JSON.stringify`方法还可以接受一个数组，作为第二个参数，指定需要转成字符串的属性。

```js
var obj = {
  'prop1': 'value1',
  'prop2': 'value2',
  'prop3': 'value3'
};

var selectedProperties = ['prop1', 'prop2'];

JSON.stringify(obj, selectedProperties)
// "{"prop1":"value1","prop2":"value2"}"
```

- 第三个参数

`JSON.stringify`还可以接受第三个参数，用于增加返回的JSON字符串的可读性。如果是数字，表示每个属性前面添加的空格（最多不超过10个）；如果是字符串（不超过10个字符），则该字符串会添加在每行前面。

- `toJSON`方法

  对象有自定义的`toJSON`方法，那么`JSON.stringify`会使用这个方法的返回值作为参数

  ```js
  var date = new Date('2015-01-01');
  date.toJSON() // "2015-01-01T00:00:00.000Z"
  JSON.stringify(date) // ""2015-01-01T00:00:00.000Z""
  ```

#### JSON.parse()方法

> ` JSON.parse`方法用于将JSON字符串转化成对象。

`JSON.parse`方法可以接受一个处理函数，用法与`JSON.stringify`方法类似。

```js
function f(key, value) {
  if (key === ''){
    return value;
  }
  if (key === 'a') {
    return value + 10;
  }
}

var o = JSON.parse('{"a":1,"b":2}', f);
o.a // 11
o.b // undefined
```

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

- 最大的好处是大大提高了代码的可维护性
- 编写代码不必从零开始。当一个模块编写完毕，就可以被其他地方引用。
- 可以避免函数名和变量名冲突

### require函数参数（string)

1. 绝对路径
2. 相对路径
3. .js可以省略（默认找.js    .json) (如果是文件夹 默认找其下的index.js)
4. 直接写字符串(引入内置模块和node_modules文件夹下的模块)

### CommonJS规范

这种模块加载机制被称为CommonJS规范。在这个规范下，每个`.js`文件都是一个模块，它们内部各自使用的变量名和函数名都互不冲突。

### 基本模块

#### child_process

- child_process.spawnSync(command,  args)
  - 使用给定的 `command` 和 `args` 中的命令行参数来衍生一个新进程

#### fs

> Node.js内置的`fs`模块就是文件系统模块，负责读写文件。

- fs.readFile(path[, options], callback)
- fs.writeFile(file, data[, options], callback)
- fs.unlink(path, callback)
- fs.stat(path, callback)
  - fs.stat(path, callback).isFile()
  - fs.stat(path, callback).isDirectory()
  - fs.stat(path, callback).isDirectory().ctime
- fs.rename(oldPath, newPath, callback)
- fs.unlink()
- fs.mkdir(path[, mode], callback)   
  - 只能建一层
- fs.rmdir(path, callback)
- fs.readdir(path[, options], callback)
- fs.watch(filename, [,options], [,listener])
- fs.createReadStream(path[, options])
- fs.createWriteStream(path[, options])
- fs.existsSync(path)

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

- 有些流用来读取数据，比如从文件读取数据时，可以打开一个文件流，然后从文件流中不断地读取数据。
- 有些流用来写入数据，比如向文件写入数据时，只需要把数据不断地往文件流中写进去就可以了。

在Node.js中，流也是一个对象，我们只需要响应流的事件就可以了：

- `data`事件表示流的数据已经可以读取了
- `end`事件表示这个流已经到末尾了，没有数据可以读取了
- `error`事件表示出错了

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

- http.createServer([requestListener])
  - http.createServer((req, res) => {})
    - req IncomingMessage 类的实例（events)  可读可写流
    - res ServerResponse 类的实例 （events)    可读可写流
- http.request(options[, callback\])

**req**

- **message**.url
  - 返回请求的 URL 字符串。 仅包含实际 HTTP 请求中的 URL

**res**

- response.end([data][, encoding][, callback])
  - 该方法会通知服务器，所有响应头和响应主体都已被发送，即服务器将其视为已完成。 每次响应都必须调用 `response.end()` 方法

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

- os.homedir()
  - 以字符串的形式返回当前用户的home目录
- os.tmpdir()
  - 返回一个字符串, 表明操作系统的 默认临时文件目录
- os.freemem()
  - 以整数的形式回空闲系统内存的字节数.
- os.totalmen()
  - 以整数的形式返回所有系统内存的字节数
- os.platform()
  - 返回一个字符串, 指定Node.js编译时的操作系统平台
- os.EOL
  - 一个字符串常量,定义操作系统相关的行末标志:
- os.getNetworkInterfaces()
  - 返回一个对象,包含只有被赋予网络地址的网络接口.

#### path



const path = require('path')

- path.join([...paths])
  - 使 用平台特定的分隔符把全部给定的 `path` 片段连接到一起，并规范化生成的路径
- path.resolve([...paths])
  - 把一个路径或路径片段的序列解析为一个绝对路径
- path.basename(path[, ext])
  - 返回一个 `path` 的最后一部分，类似于 Unix 中的 `basename` 命令
- path.extname(path)
  - 返回 `path` 的扩展名，即从 `path` 的最后一部分中的最后一个 `.`（句号）字符到字符串结束
- path.parse(path)    // 字符串到某数据类型的转换
  - 返回一个对象，对象的属性表示 `path` 的元素
- path.format(pathObject)   // 从某数据类型到字符串的转换
  - 从一个对象返回一个路径字符串。 与 [`path.parse()`](http://nodejs.cn/api/path.html#path_path_parse_path) 相反
- path.sep
  - 提供了平台特定的路径片段分隔符
- path.delimiter
  - 提供平台特定的路径分隔符

### 事件循环机制（Event Loop）

- 时间相关的
- 网络请求相关的函数

被设计为异步

![Event Loop](http://image.beekka.com/blog/2014/bg2014100802.png)

### 全局变量

- __dirname  //绝对路径
- __filename   //绝对路径
- setImmediate(fn) = setTimeout(fn, 0)      
  - 把同步转化为异步
- process.argv
  - `process.argv` 属性返回一个数组，这个数组包含了启动Node.js进程时的命令行参数。第一个元素为[`process.execPath`](http://nodejs.cn/api/process.html#process_process_execpath)。第二个元素为当前执行的JS文件路径。剩余的元素为其他命令行参数

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

### 单页面应用（Single Page Appliction  简称SPA）

> 指在**浏览器中运行的应用**，根据前端路由（hash）来显示不同的内容，所有数据交互由ajax完成， 在使用期间**不会刷新页面**。

#### 优点

- 无刷新体验

  > 这个应该是最显著的有点，由于路由分发直接在浏览器端完成，页面是不刷新，对用户的响应非常及时，因此提升了用户体验；

- 完全的前端组件化

  > 前端开发不再以页面为单位，更多地采用组件化的思想，代码结构和组织方式更加规范化，便于修改和调整；

- API 共享

  > 如果你的服务是多端的（浏览器端、Android、iOS、微信等），单页应用的模式便于你在多个端共用 API，可以显著减少服务端的工作量。容易变化的 UI 部分都已经前置到了多端，只受到业务数据模型影响的 API，更容易稳定下来，便于提供鲁棒的服务；

- 组件共享

  > 在某些对性能体验要求不高的场景，或者产品处于快速试错阶段，借助于一些技术（Hybrid、React Native），可以在多端共享组件，便于产品的快速迭代，节约资源。

#### 缺点：

- 首次加载大量资源，

  > 要在一个页面上为用户提供产品的所有功能，在这个页面加载的时候，首先要加载大量的静态资源，这个加载时间相对比较长；

- 较高的前端开发门槛

  > MVC 前置，对前端工程师的要求提高了，不再是『切切图，画画页面这么简单』；同时工作量也会增加数倍，开发这类应用前端工程师的数量往往多于后端；

- 不利于 SEO

  > 单页页面，数据在前端渲染，就意味着没有 SEO，或者需要使用变通的方案。

前端路由

> 前端路由的实现其实很简单。本质上就是检测 url 的变化，根据不同的url来展示不同的页面
>
> 在14 年之前，大家是通过 hash 来实现路由， hash 值的变化，并不会导致浏览器向服务器发出请求，浏览器不发出请求，也就不会刷新页面。另外每次 hash 值的变化，还会触发 `hashchange` 这个事件，通过这个事件我们就可以知道 hash 值发生了哪些变化，检测到 hash 的变化后，就可以通过替换 DOM 的方式来实现页面的更换
>
> 14年后，因为HTML5标准发布。多了两个 API，`pushState` 和 `replaceState`，通过这两个 API 可以改变 url 地址且不会发送请求。同时还有 `onpopstate` 事件。通过这些就能用另一种方式来实现前端路由了，但原理都是跟 hash 实现相同的。用了 HTML5 的实现，单页路由的 url 就不会多出一个`#`，变得更加美观。但因为没有 `#` 号，所以当用户刷新页面之类的操作时，浏览器还是会给服务器发送请求。为了避免出现这种情况，所以这个实现需要服务器的支持，需要把所有路由都重定向到根页面。（**history 模式**）

后端路由

promise()      (then)







ToDo  node.js  清理超过3小时文件

fs.stat

fs.unlink