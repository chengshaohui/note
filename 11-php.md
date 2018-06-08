# php笔记

##  导读

* wamp  
    * 集成开发环境
    * w：windows   操作系统    mamp    lamp
    * a：apache 服务器   //   提供某种特定功能的代码块  web服务器 发送/接收请求
    * m：mysql  数据库服务   //  关系型/非关系型 （MongoDB） 关系模型 
    * p:  php  是运行在服务器端的脚本语言
* 静态网页
    * 没有链接数据库的网页
* 动态网页     
    * 链接数据库，数据库中获取数据   
### 服务器如何处理用户请求
当在地址栏键下地址的时候，浏览器会结合我们的软硬件，将http请求发送到网络中，服务器接收到我们的请求，开始处理我们的请求，请求的资源分为静态资源和动态资源，静态资源像：.html, .css, .js等这些后缀名的文件，动态资源像.php,.java等这些资源，服务器碰到请求是静态资源会直接返回，碰到动态资源会先解析，php文件最终输出的内容将会交给服务器，最后服务器返回输出的内容，当浏览器接收到返回的内容，开始绘制，碰到href,src,url这些东西的时候，会再次向服务器发送请求，最终呈现整个页面
> 静态资源   .html  .css  .js  .jpg  .gif  .png  以字符串的形式直接返回，不做处理
> 动态资源    .php  .jsp    (php)解析器处理文件    把echo的东西返回
##php
###php是什么？
超文本预处理语言，运行在服务器端，能和html进行嵌套用于制作动态网页的语言
###php特点
  * 运行在服务器端的脚本语言
  * 能支持绝大部分的操作系统
  * 能支持大部分的服务器  apache  IIS
  * 能支持大部分的数据库  mysql  sql sever   Access
  * 能操作数据库
  * 能操作文件
  * 能操作图片
  * ...
###php基本语法

> exit 结束运行  可以用来调错
>
> die() 结束运行

####变量和常量
##### 输出php的两种方式
    1. echo              输出字符串
    2. var_dump()   输出类型和值
##### 错误的几种情况
      1. error 致命性的错误  停止执行
      2. notice   错误  继续执行
      3. warning  错误  继续执行
#####定义变量
```php
    $str = '123';
    var_dump($str);  //string '123' (length=3)
```
#####定义常量
```php
    // define("PI", 3.14);
    const PI = 3.14;
    var_dump(PI);
```
#####常量和变量的区别
  * 常量的值不能再改变或者是被删除
  * 常量不加$
  * 常量只能用const或者是define来定义
  * 常量可以在任何位置去访问
  * 常量的值不能延迟求值，只能是标量(const 不可以，define可以)
#####判断变量和常量是否被定义
  * 判断一个变量有没有定义用isset()
  * 判断一个常量有没有定义用defined()
  * 当一个变量值为null的时候。被认为是没有定义
```php
	var_dump($nub = null); 
	var_dump(isset($nub)); 
    const PI = 123; 
	var_dump(defined('PI')); 
```
#####删除变量
   unset()
```php
  $num = 200;
  // $num = null;
  unset($num);  
  var_dump($num);  //notice  null
```
#####变量引用  &
```php
  $nub1 = 200;
  $nub2 = $nub1;
  $nub1 = 300;
  echo $nub2; //200
-----------------------------------------------------------
  $nub1 = 200;
  $nub2 = &$nub1;
  $nub1 = 300;
  echo $nub2; //300
```
 #####可变变量
```php
  $nub = "age";
  $$nub = "123";
  var_dump($$nub);   // string '123' (length=3)
```
####数据类型
> 4种标量   2种复合类型   2种特殊类型
##### 4种标量

* 整型  int 
* 浮点型  float    也作double
* 字符串   string
  * . 表示连接      //可以连接两个标量类型，连接成字符串
  * ""可以解析变量
  * ```php
       $nub = 200;
       $str1 = "这是一个数字{$nub}nub"; //""可以解析变量
       $str2 = '这是一个数字'.$nub;  //. 表示连接,可以连接两个标量类型，连接成字符串
       var_dump($str1, $str2)  //string '这是一个数字200nub' (length=24)
        //string '这是一个数字200' (length=21)
       ```
* 布尔类型  boolean

##### 2种复合类型

###### 数组

* 数组的长度
  ```php
      $arr = array('a', 'b', 'c');
      var_dump(count($arr)) ;//数组的长度
  ```

* 索引数组
  ```php
      echo "<pre>";
      $arr = array("a", "b", "c");
      var_dump($arr);  /*array (size=3)
                         0 => string 'a' (length=1)
                         1 => string 'b' (length=1)
                         2 => string 'c' (length=1)
      print_r($arr);  /*Array
                          (
                                [0] => a
                                [1] => b
                                [2] => c
                         )
  ```

* 关联数组
  ```php
      $crr = array(
          'name' => 'lisi', 
          'age' => 13
      ); /* array (size=2)
           'name' => string 'lisi' (length=4)
           'age' => int 13
  ```

* 二维数组
  ```php
    $brr = array(
      'name' => array(
        'lisi' => '13',
        'zhangsan' => '24'
        ),
      'age' => 18
    ); 
  ```

* 遍历方式
    ```php
      for ($i=0; $i < count($arr); $i++) { 
          var_dump($arr[$i]);
      }
    ```
    ```php
    $arr = array('name' => 'lisi', 'age' => 13);
    foreach ($arr as $key => $value) {
    	var_dump($arr[$key]); //lisi   13
    	var_dump($key);   //name age
    	var_dump($value); //lisi 13
    }
    ```

###### 对象



##### 2种特殊类型

* null    //函数默认返回值 变量未定义  unset()  
* resource
  * 引用
  * is_resource()    //判断是否是资源

#####获取、判断、转化类型的方式
   * 获取类型
      * gettype()

* 判断类型

     * is_int 
     * is_integer 
     * is_float 
     * is_double
     * is_string 
     * is_bool 
     * is_array 
     * is_object 
     * is_null
     * is_resource

* 类型转化

     * val

          * intval()
          * floatval()
          * doubleval()
          * strval()              ```//  将true转化为1，将false转化为'';```
          * boolval()           ```  //  false   0    '0'    ''    null    空数组```

     * 强制类型转化

          ```php
          $nub = '123';
          $result = (int) $nub;
          var_dump($result);  //int 123
          ```

     * settype   //不建议 因为会改变原来的类型



### 对象

> js：属性和方法
> PHP：成员变量和成员方法

#### 面向过程\对象编程 

- 面向过程编程

  > 一个功能对应一个函数，需要什么样的功能，写什么样的函数

- 面向对象编程 

  > 将整个项目中的每一部分抽象为一个对象，只需关注对象和对象之间的联系,然后实现对象的成员方法，从而构建整个项目

#### 对象和类的关系

##### 类是对象的抽象

> 我们将具有某种相似特征的对象的基础上，抽象为一个用来描述或者用来创建这些对象的类，所以我们说类是对象的抽象，比如说，我们将所有的人的特征抽象为人类的这个概念

##### 对象是类的实例化

> 有了包含一些特征的抽象出来的类以后，那么我们可以通过这个类，去创建对象，所以说对象是类的实例化，比如说小明是人类的一个实例

#### 封装、继承、多态

##### 封装

> 我们将对象的成员变量或者成员方法通过一些关键字，比如  public private protected 等去封装在类的内部，只留和外界的接口

* 强内聚      //我们倾向于将更多的方法或者是变量封装在类的内部
* 低耦合      //我们倾向于将更少的方法暴露在外部

##### 继承

> 一个类继承于另外一个类，从而获取这个类的成员变量和方法，通过 extends 去继承
>  子类   父类

##### 多态

> 不同的对象调用同一个方法，或者是相同的操作，结果不同，就是多态

#### 实例

```php

```



### 常用方法

####字符串方法

| 方法             | 描述                       | 例子                                       |
| -------------- | ------------------------ | ---------------------------------------- |
| strlen()       | 字符串长度                    | \$result = strlen('length');            var_dump($result);    // 6 |
| explode()      | 把字符串分割成数组                | \$result = explode('.' , 'aa.jpg');  var_dump($result);      // array('aa', 'jpg') |
| substr()       | 从当前字符串截取指定位置到指定长度的新字符串   | \$str = 'dfsdg';     \$result = substr(\$str,-3,1);      var_dump(\$result); // 's' |
| mb_substr()    | 字符数    可以转化编码            | \$str = '字符串';\$result = mb_substr(\$str,3,1,'utf8');         var_dump($result);  // '符串' |
| strstr()       | 返回从当前字符串中匹配到的第一个字符之后的字符串 | \$str = 'fghg';    \$result = strstr(\$str,'h',true);      var_dump(\$result); // 'hg' |
|                |                          |                                          |
| strpos()       | 查找指定字符首次出现的位置，返回索引值      |                                          |
| strrpos()      | 查找指定字符最后一次出现的位置，返回索引值    |                                          |
| str_replace()  | 替换 （字符串和字符串，数组和字符串）      |                                          |
| str_ireplace() | 替换，不区分大小写                |                                          |
|                |                          |                                          |
| md5()          | 计算字符串的 MD5 散列   用于加密     |                                          |
| strrev()       | 反转字符串顺序                  |                                          |
|                |                          |                                          |
| strtolower()   | 小写                       |                                          |
| strtoupper()   | 大写                       |                                          |
|                |                          |                                          |
| trim()         | 去两端空格                    |                                          |
| rtrim()        | 去右端空格                    |                                          |
| ltrim()        | 去左端空格                    |                                          |



####数组方法

| 方法                 | 作用                                  | 例子     |
| ------------------ | ----------------------------------- | ------ |
| array_push()       | 在数组后面推入新项                           | `````` |
| array_pop()        | 删除数组最后一项                            |        |
| array_shift()      | 删除数组前面一项                            |        |
| array_unshift()    | 在数组前面推入新项                           |        |
|                    |                                     |        |
| array_sum()        | 数组项求和                               |        |
| array_merge()      | 合并数组  如果有相同的键值那么后者就会覆盖前者            |        |
| array_unique()     | 去重                                  |        |
| array_rand()       | 随机取键   在一个数组中取随机的键，如果取多个，返回的是键组成的数组 |        |
|                    |                                     |        |
| in_array()         | 判断某个值在不在数组里 是否启用全等                  |        |
| array_search()     | 查找某个值对应的键  返回索引值  若找不到返回false       |        |
| array_key_exists() | 判断某个值是不是数组的键，在返回true，不在返回false      |        |
|                    |                                     |        |
| array_filter()     | 筛选   返回值是新数组，接收回调函数                 |        |
| array_walk()       | 遍历   将每一个值都执行一个函数                   |        |
| array_map()        | 映射                                  |        |
|                    |                                     |        |
| array_keys()       | 键组成数组  如果有第二个参数，那么只会返回与第二个参数匹配的键    |        |
| array_values()     | 返回 值组成的数组                           |        |
|                    |                                     |        |
| sort()             | 升序  会影响原数组                          |        |
| rsort()            | 降序                                  |        |
| asort()            | 升序    键不重排                          |        |
| arsort()           | 降序    键不重排                          |        |
| ksort()            | 按键 升序                               |        |
| krsort()           | 按键 降序                               |        |

​	

####Math方法

| 方法      | 作用          |      |
| ------- | ----------- | ---- |
| abs()   |             |      |
| ceil()  |             |      |
| floor() |             |      |
| max()   |             |      |
| min()   |             |      |
| round() |             |      |
| mt_rand | 随机数         |      |
| pow()   | 返回 x 的 y 次方 |      |



### 函数

#### 参数

* 如果定义了形式参数，必须传实际参数
* 检测函数是否存在
* 可变函数

#### 作用域

* 全局变量只能在全局访问，局部变量只能在局部访问
* 常量在任何位置都可以访问
* 超全局变量在任何位置都可以访问 
  * $_GLOBALS
  * $_GET
  * $_POST
  * $_REQUEST      //get()方法  post()方法    都可以接受
  * $_FILES
  * $_SERVER
  * $_SESSION   服务器端session
  * $_COOKIE


* 在函数内部访问全局变量的三种方式

```php
//第一种方式
    $nub = 200;
    function fun(&$aa)
    {
        $aa = 300;
        echo $aa; //300
    }
    fun($nub);
    echo $nub; //300

//第二种方式
    $nub = 200;
    function fun()
    {
        global $nub;
        $nub = 300;
        echo $nub; //300
    }
    fun();
    echo $nub; //300

//第三种方式
    $nub = 200;
    function fun()
    {
        $GLOBALS['nub'] = 300;
        echo $GLOBALS['nub'];  // 300
    }
    fun();
```

#### 注意

```php
//
  header(string: 'content-type:text/html;charset=utf8');
//   
  echo true;          //1
  echo false;         //null
  var_dump((int) 'a');     //0

// 实现代码块复用
	include '';         //不建议用
	include_once '';    //报warning
	require_once '';    //报error

// 回调函数
	function callback()
	{
		return 3;
	}
	function fun($callback)
	{
		echo($callback());
	}
	fun('callback'); //3

// 静态变量
    function fun()
    {
        static $nub = 200;  //静态变量
        $nub += 1;
        echo $nub;
    }
    fun(); //201
    fun(); //202
    fun(); //203
```



### 时间函数

>  北京时间 = GMI + 8

#### 方法

* date_default_timezone_get() 

  * ```php
    var_dump(date_default_timezone_get());  // string 'UTC' (length=3)
    ```

* date_default_timezone_set()     

  * ```php
    date_default_timezone_set('Asia/Shanghai');
    ```

* time()                  // 距离1970年的秒数

  * ```php
     var_dump(time())      //int 1506652819
     ```
    ```

    ```

* microtime(true)        // 微秒

  * ```php
    var_dump(microtime())        //string '0.04552800 1506652891' (length=21)

    var_dump(microtime(true))    //float 1506652947.956
    ```

* getdate()            // 当前时间的细节组成的数组

  * ```php
    var_dump(getdate()); 
    array (size=11)
      'seconds' => int 28
      'minutes' => int 43
      'hours' => int 2
      'mday' => int 29
      'wday' => int 5
      'mon' => int 9
      'year' => int 2017
      'yday' => int 271
      'weekday' => string 'Friday' (length=6)
      'month' => string 'September' (length=9)
      0 => int 1506653008
    ```

* date()   // 格式化时间

  * ```php
    date_default_timezone_set('Asia/Shanghai');
    var_dump(date("Y-m-d H:i:s"));     // string '2017-09-29 11:07:48'
    ```

* mktime()   // 设置时间

  * ```php
    var_dump(mktime(8,0,0,8,8,2008));  // int 1218182400

    $time = mktime(8,0,0,8,8,2008);
    $arr = getdate($time);
    var_dump($arr);
    	/*
          array (size=11)
            'seconds' => int 0
            'minutes' => int 0
            'hours' => int 8
            'mday' => int 8
            'wday' => int 5
            'mon' => int 8
            'year' => int 2008
            'yday' => int 220
            'weekday' => string 'Friday' (length=6)
            'month' => string 'August' (length=6)
            0 => int 1218182400
        */

    $str = date('Y-m-d H:i:s', $time);
    var_dump($str);  //string '2008-08-08 08:00:00' (length=19)
    ```

```php
/*a: 'am'
d： 几日，两位数字
D: 星期几，3个英文字母
F: 月份，英文全名
h: 12小时制的小时
H: 24小时制的小时
g: 12小时制的小时 不补零
G: 24小时制的小时 不补零
j: 几日，不足不补零
l: 星期几，英文全名
m: 月份，两位数字
n: 月份，两位数字 不补零
M: 月份，3个英文字母
s: 秒;
S: 字尾加英文序数，   ‘21th’
t: 指定月份的天数
U: 总秒数
w: 数字型的星期几 0-6
Y: 年  四位数字
y: 年  两位数字
z: 一年中的第几天; 1-366*/
```

### cookie

> cookie 常用于识别用户。cookie 是一种服务器留在用户计算机上的小文件。每当同一台计算机通过浏览器请求页面时，这台计算机将会发送 cookie。通过 PHP，您能够创建并取回 cookie 的值。



#### 创建 Cookie

* setcookie() 函数用于设置 cookie

* setcookie() 函数必须位于 <html> 标签之前

* ```
  语法   setcookie(name, value, expire, path, domain);

  例子	 setcookie("user", "runoob", time()+3600);
  ```

#### 取回 Cookie 的值

* PHP 的 $_COOKIE 变量用于取回 cookie 的值

```php
<?php
// 输出 cookie 值
echo $_COOKIE["user"];

// 查看所有 cookie
print_r($_COOKIE);
?>
```

#### 删除 Cookie

* 当删除 cookie 时，您应当使过期日期变更为过去的时间点

```php
// 设置 cookie 过期时间为过去 1 小时
setcookie("user", "", time()-3600);
?>	
```

### session



### Filesystem 函数

##### 魔术常量

* \__dir__   当前路径
* \__file__   全路径        当前路径+文件名
* \__line__ 运行代码的当前行

##### PHP  Filesystem 函数

| 方法            | 描述                      | 例子   |
| ------------- | ----------------------- | ---- |
| basename()    | 从一个路径中 返回文件名            |      |
| dirname()     | 从一个路径中 返回路径             |      |
| file_exists() | 判断文件或者路径存在不存在           |      |
| is_file()     | 判断这是不是文件      只能识别当前路径  |      |
| is_dir()      | 判断这是不是路径       只能识别当前路径 |      |
| rmdir()       | 删除空路径                   |      |
| unlink()      | 删除文件                    |      |
|               |                         |      |

```php
is_file() is_dir()   如果需要认识上一级或是下一级，需要写相对路径
```



### PHP Directory 函数

> Directory 函数允许您获得关于目录及其内容的信息

| 方法        | 描述                          | 例子   |
| --------- | --------------------------- | ---- |
| scandir() | 返回指定目录中的文件和目录的数组  '.'  '..' |      |
|           |                             |      |
|           |                             |      |



# mysql

能够永久存储信息的字段

SQL        结构化查询语言             操作数据库

## 定义语言

### 展示库/表：

* show databases;
* show tables;
* show create table aa;                                        // 展示创建表的过程
* show create database 206class;                      // 展示创建库的过程
* desc  206class                                                     // 展示表 \ 库

### 创建库/表

* #### 创建库

```sql
create  database   206class  charset utf8 ;    //建立新数据库    数据存储有很多种方式
```

* #### 创建表

```sql
use 206class
mysql> create table student (
    -> id tinyint(10) unsigned not null primary key auto_increment,
    -> name char(100) not null unique key,
    -> grade float(5,2) not null default 0.00,
    -> updatetime datetime on update current_timestamp not null
    ->  ) engine=innodb default  charset = utf8;	
// 存储引擎（决定存储效率、安全性）innodb[安全性高、效率低]   myisam[安全性低、效率高]     字符集
```

#### 增加字段

```sql
alter table student add num char(20) not null;
```

#### 删除表/库/字段

- 删除表 \ 库

```sql
drop  database myclass  \   drop table student 
```

- 删除字段

```sql
alter table student drop num;
```

#### 修改表名、字段

* 修改表名

```mysql
use myclass;
rename table aa to user;
```

* 修改字段

```sql
 alter table student change grade grades int(10) not null;
 
 alter table student modify grades float(5,2) not null;
 
 alter table student modify updatetime datetime default current_timestamp on update current_timestamp;
```

## 操作语言

### 1. 增

* 插入数据

```sql
insert into student (name) values ('小马');   
//insert into 表（字段） value (要插入的数据一一对应); 

insert into student (name) values ('小员'),('小程');

insert into student (name,grade) values ('小黑',100);
```

### 2. 删

* 删除某一行数据 delete  


```sql
delete from user;     //全删除了

delete from user where  id = 7;
```

### 3. 改

* 更新 update

```sql
update user set pass=123 ;   // 所有

update user set pass=456 where id=10;

update user set pass=789,username='newuser2' where id=10;
```

### 4. 查   80-90%

#### 基本查询

> where      group by       having       order by        limit
>
> where 查询原字段     having查询筛选结果



##### 查询表中所有数据

```sql
use myclass;
select * from student;                      //select 字段  from 表
```

##### where筛选 原字段 查指定数据

* =   >=   <=   <>    >    < 

  ```
  select * from student where id>=5; 
  ```

* and or  between   in

  ```sql
  select * from student where id>4 and id<5;   or  

  select * from student where id between 8 and 10;
  select * from student where id>=8 and id<=10;
  select * from user where id in (1,2,10,11);
  ```

* 模糊查询

  ```sql
  %任意字符
  select * from goods where name like '%电';   // 所有以 电 结尾字段
  select * from goods where name like '%电%';  // 所有带 电 的的字段
  select * from goods where name like '电%';   // 所有以 电 开头的字段

   _单个字符
  select * from goods where name like '电_';   \ 电 + 一个字符  的字段
  select * from goods where name like '电__';  \ 电 + 两个字符  的字段
  ```

* 查null

  ```sql
  select * from goods where name is null;
  select * from goods where name is not null;
  ```

##### 投影运算

```sql
select id,name from student; 

select id,name,(shop_price-price)*count as profit from goods;
select id,name, floor((shop_price-price)*count) as profit from goods;  // 利润向下取整
select id,name,shop_price-price from goods where shop_price-price>200;  //利润超过200
```

##### having查询

```sql
select id,name,shop_price-price from goods where shop_price-price>200; //重复查询

select id,name,shop_price-price as profit from goods having profit>200; //having

select id,name,shop_price-price as profit from goods where id>4 having profit>200;
```

##### max、mix、num、avg、count

```sql
// 和id... 不对应

select sum(count) as he from goods;     
select min(shop_price) as minval from goods;
select avg(shop_price) as avgval from goods;
select max(shop_price) as maxvak from goods;
select count(shop_price) as countval from goods;
```

##### 分组查询

```sql
 select * from goods group by type;
 select count(type) from goods group by type;     // 每一组的个数
 select sum(count) from goods group by type;      // 某个列的和
 select max(count) from goods group by type;      // 某个列的最大值
 select max(count),type from goods group by type;  // 某个列的最小值   // 查询正确 
 select max(count),id from goods group by type;    // 某个列的最小值   // 查询错误
```

##### order查询

```sql
select * from goods order by price desc;     asc desc(降序)
```

##### limit查询

```sql
select * from goods order by count desc limit 3;

select * from goods order by count desc limit 4,2;   //隔4行取两个   可以用于分页
select * from goods order by count desc limit 10*n,10;   //隔10页取10个  用于分页
```

##### where子查询

> where型子查询是将上一次查询的结果作为条件

```sql
select id,name from goods where count=(select max(count) from goods);
select id,name from goods where count in (select count from goods where id>3);
```

##### from子查询

> from型子查询是将上一次查询的结果作为临时的一张表

```sql
select name from (select id,name from goods) as tmp;

select name from (select id,name from goods) as tmp where id > 3 ;
select name from (select id,name from goods where id > 3) as tmp;
```

##### exists子查询

```sql
select * from goods where exists (select * from goods where id=1);   //整个表的数据

select * from goods where exists (select * from goods where id=7);   //Empty set (0.00 sec)
```

#### 连表查询

##### 内链接

> 作用：根据两个或多个表中的列之间的关系，从这些表中查询数据。
>
> 注意: 内连接是从结果中删除其他被连接表中没有匹配行的所有行，所以内连接可能会丢失信息。
>
> 重点：内连接，只查匹配行。

```sql

select news.*, user.username as uname from news inner join user on news.uid=user.id;

```

##### 外连接

> 与内连接相比，即使没有匹配行，也会返回一个表的全集。
>
> 外连接分为三种：左连接，右连接，全连接。对应SQL：left/right/full outer join。通常我们省略outer 这个关键字。写成：left/right/full。
>
> 重点：至少有一方保留全集，没有匹配行用NULL代替。

###### 1）left join，左连接

> 结果集保留左表的所有行，但只包含第二个表与第一表匹配的行。第二个表相应的空行被放入NULL值。

```sql
select * from news right join user on news.uid=user.id;  //
```

###### 2）right join，右连接

> 右外连接保留了第二个表的所有行，但只包含第一个表与第二个表匹配的行。第一个表相应空行被入NULL值。

```sql
select * from news left join user on news.uid=user.id;   
```

* 权限管理
* 主键 （自增）  唯一标识信息   id   



* 内容管理系统 cms


## MVC

### 1、概念

​        MVC全名是Model View Controller，是模型(model)－视图(view)－控制器(controller)的缩写，一种软件设计典范，用一种业务逻辑、数据、界面显示分离。

​        MVC就是类似三层的一种架构，主要还是采用封装（分层）的思想，来降低耦合度，从而使我们的系统更加的灵活，扩展性更好。

### 2、内容

​      Model（模型）是应用程序中用于处理应用程序数据逻辑的部分。通常模型对象负责在数据库中存取数据。
​      View（视图）是应用程序中处理数据显示的部分。通常视图是依据模型数据创建的,用来展示呈现数据
​      Controller（控制器）是应用程序中处理用户交互的部分。通常控制器，接收请求，定义要做的事情。选择相应的模型，选择相应的视图。

### 3、优点

​       （1）提高代码的复用性。
​       （2）将整个系统划分为三层，有效的实现了数据和视图的分离
​       （3） 提高整个系统的逻辑性

浏览器发送请求，控制器接收到请求，向模型发出指令，模型对象在数据库中存取数据后，返回给控制器，控制器再向view中发送结果，由view层输出数据，浏览器解释执行

