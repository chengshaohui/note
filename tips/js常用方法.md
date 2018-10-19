[TOC]

## 数组方法

> \* 代表影响原数组

|  数组方法   | 作用                                                         | 例子                                                         |
| :---------: | ------------------------------------------------------------ | :----------------------------------------------------------- |
|   push()*   | 在数组后端添加任意个项并返回新数组的长度                     | let arr = [1, 4, 3]           result = arr.push('a', 'b')         console.log(arr, result)     // [1, 4, 3, 'a', 'b']    5 |
|   pop()*    | 移除数组中最后一项并返回该项                                 | let arr = [1, 4, 3]           result = arr.pop()                         console.log(arr, result)     // [1, 4]      3 |
|  shift()*   | 移除数组中第一个项并返回该项                                 | let arr = [1,4,3]             result = arr.shift()                                          console.log(arr, result)       // [ 4, 3]      1 |
| unshift()*  | 在数组前端添加任意个项并返回新数组的长度                     | let arr = [1,4,3]             result = arr.unshift('a', 'b')                            console.log(arr, result)   //  ['a', 'b', 1, 4, 3]   5 |
|             |                                                              |                                                              |
|   join()    | 只接受一个参数，即用作分隔符的字符串，然后返回包含所有数组项的字符串（默认，连接） | let arr = [1, 4, 3]            result = arr.join('&')            console.log(arr, result)   //  [1, 4, 3]    '1&4&3'        let arr = [1, 4, 3]            result = arr.join()                    console.log(arr, result)    // [1, 4, 3]   '1, 4, 3' |
|             |                                                              |                                                              |
|  concat()   | 先创建当前数组的一个副本，然后将接收到的参数添加到副本末尾，最后返回新构建的数组 | let arr = [1,4,3]              result = arr.concat('a', 'b')                                      console.log(arr, result)    // [1, 4, 3]   \[1, 4, 3, "a", "b"] |
|             |                                                              |                                                              |
|  splice()*  | 从数组中删除、添加项目，然后返回被删除的项目arr.splice(index,num,item1,..,itemX) | let arr = [1,4,3]             result = arr.splice(1,1,'a','b')                         console.log(arr, result)   // [1, "a", "b", 3]    \[4] |
|   slice()   | 从已有的数组中返回选定的元素。接受一个或两个参数，即要起始位置和结束位置，不影响原数组 arr.slice(index1,index2) | let arr = [1,4,3]             result = arr.slice(0,2)                                    console.log(arr, result)      // [1, 4, 3]     \[1, 4] |
|             |                                                              |                                                              |
|   sort()*   | 按升序排列数组项                                             | let arr = [1,4,3]              result = arr.sort()                                          console.log(arr, result)     // [1, 3, 4]      \[1, 3, 4] |
| reverse()*  | 反转数组项的顺序                                             | let arr = [1,4,3]              result = arr.reverse()                                     console.log(arr, result)     // [3, 4, 1]      \[3, 4, 1] |
| includes()  | 判断一个数组是否包含一个指定的值，如果是，酌情返回true或false | let arr = [1,4,3]              result = arr.includes(1)                                                        console.log(arr, result)     // [1, 4, 3]     true |
|             |                                                              |                                                              |
|             |                                                              |                                                              |
|   find()    | 返回数组中满足提供测试函数的第一个元素的值。否则返回undefined | let arr = [1,4,3]              result = arr.find(v => v > 2)     console.log(arr, result)        // [1, 4, 3]    4 |
| findIndex() | 返回数组中满足提供测试函数的第一个元素的索引。否则返回-1     | let arr = [1,4,3]     result = arr.findIndex(v => v > 0)                    console.log(arr, result)        // [1, 4, 3]     0 |
|             |                                                              |                                                              |
|  filter()   | 对数组中的每一项运行给定函数，返回该函数会返回true的项组成的数组 | let arr = [1,4,3]              result = arr.filter(v => v > 1)            console.log(arr, result)        // [1, 4, 3]    \[4, 3] |
|  forEach()  | 对数组中的每一项运行给定函数，这个方法没有返回值     主要用来遍历数组 | let arr = [1,4,3]              result = arr.forEach(v=> v + 1)                console.log(arr, result)       // [1, 4, 3]   undefined |
|    map()    | 映射 返回什么样的值，形成什么样的集合                        | let arr = [1,4,3]              result = arr.map(v=> v * 2)              console.log(arr, result)       // [1, 4, 3]    \[2, 8, 6] |
|             |                                                              |                                                              |
|   some()    | 对数组中的每一项运行给定函数，如果该函数对任一项返回true，则返回true | let arr = [1,4,3]             result = arr.some(v=> v > 3)          console.log(arr, result)      // [1, 4, 3]  true |
|   every()   | 对数组中的每一项运行给定函数，如果该函数对每一项都返回true，则返回true | let arr = [1,4,3]             result = arr.every(v => v > 3)    console.log(arr, result)      // [1, 4, 3]  false |



## 字符串方法

| 字符串方法        | 描述                                                         | 例子                                                         |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| charAt()          | 以单字符字符串的形式返回给指定位置的那个字符                 | let str = 'hello world'       result = str.charAt(1)                 console.log(str, result)         //  'hello world'    'e' |
| charCodeAt()      | 返回给指定位置的那个字符的字符编码                           | let str = 'hello world'     result = str.charCodeAt(1)  console.log(str, result)         //  'hello world'   101 |
| fromCharCode()    | 接收一个或多个字符编码，然后将它们转化成一个字符串           | result = String.fromCharCode(104, 101, 108, 108, 111)           console.log(result)               //  'hello' |
|                   |                                                              |                                                              |
| concat()          | 用于将一个或多个字符串拼接起来，返回拼接的到的新字符串，不改变原先的字符串的值   可以接受任意多的参数 | let str = 'hello'       result = str.concat(' world', '!')                          console.log(str, result)   // 'hello'   'hello world!' |
| replace()         | 接受两个参数，第一个参数可以是RegExp对象或者一个字符串，第二个参数可以是一个字符串或者一个函数。如果第一个参数是字符串，那么只会替换第一个子字符串 | let str= 'hello world'  result=str.replace('he', 'she')      console.log(arr, result)    // 'hello world'  'shello world' |
|                   |                                                              |                                                              |
| split()           | 这个方法可以基于指定的分隔符将一个字符串分割成多个字符串，并将结果放在一个数组中 | let str = 'hello world'      result = str.split(' ')                                                                                console.log(str, result)     // 'hello world' ['hello', 'world'] |
| substr()          | 返回一个字符串中从指定位置开始到指定字符数的字符             | let str = 'hello world'      result = str.substr(3, 2)                      console.log(str, result)       //  'hello world'    'lo' |
| substring()       | 返回一个字符串在开始索引到结束索引之间的一个子集, 或从开始索引直到字符串的末尾的一个子集 | let str= 'hello world'     result = str.substring(0, 3)          console.log(str, result)       //  'hello world'    'hel' |
|                   |                                                              |                                                              |
| indexOf()         | 从一个字符串中开头向后搜索给定的子字符串，然后返回子字符串的位置（如果没有找到该子字符串，则返回-1）可接受第二个参数，表示从字符串的哪个位置开始向后搜索 | let str = 'hello world '        result = str.indexOf('e')             console.log(str, result)      //  'hello world'   1                               let str = 'hello world'         result = str.indexOf('a')                     console.log(str, result)     //  'hello world'   -1 |
| lastIndexOf()     | 从一个字符串中末尾向前搜索给定的子字符串，然后返回子字符串的位置（如果没有找到该子字符串，则返回-1）可接受第二个参数，表示从字符串的哪个位置开始向前搜索 | let str = 'hello world '   result = str.lastIndexOf('e')     console.log(str, result)     // 'hello world'    1                         let str = 'hello world '   result = str.lastIndexOf('a')            console.log(str, result)     //  'hello world'   -1 |
|                   |                                                              |                                                              |
| slice(start, end) | 提取字符串的一部分，并返回一新的字符串                       | let str = 'hello world'       result = str.slice(1, 3)                                                          console.log(str)                 //   'hello world'     'el'                             let str = 'hello world'       result = str.slice(-4, -1)                     console.log(str, result)     //   'hello world'    'orl' |
|                   |                                                              |                                                              |
| startsWith()      | 用来判断当前字符串是否是以另外一个给定的子字符串“开头”的，根据判断结果返回 true 或 false。 | let str = 'hello world'   result = str.startsWith('he')                console.log(str, result)      //  'hello world'   true |
| endsWith()        | 用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false | let str = 'hello world'      result = str.endsWith('d')           console.log(str, result)     //  'hello world'   true |
| includes()        | includes() 方法用于判断一个字符串是否包含在另一个字符串中，根据情况返回true或false | let str = 'hello world'      result = str.includes('o')          console.log(str, result)     //   'hello world'  true |
|                   |                                                              |                                                              |
| toLowerCase()     | 字符串转化为小写                                             | let str = 'Hello World'    result = str.toLowerCase()                                console.log(str, result) //Hello World  hello world |
| toUpperCase()     | 字符串转化为大写                                             | let str='Hello'              result = str.toUpperCase()                   console.log(str, result)     //'Hello'  'HELLO' |
|                   |                                                              |                                                              |
| trim              | 创建一个字符串的副本，删除前置及后缀的所有空格，然后返回结果 | let str = '   hello  '             result = str.trim()    console.log(str, result)   // '   hello   '   'hello' |
| trimLeft          | 从一个字符串的左端移除空白字符。                             | let str = '   hello  '             result = str.trimLeft()    console.log(str, result)   // '   hello   '   'hello  ' |
| trimRight         | 从一个字符串的右端移除空白字符                               | let str = '   hello  '             result = str.trimRight()    console.log(str, result)   // '   hello   '   '   hello' |

## Math方法

| Math方法             | 描述                                                         | 例子                                               |
| -------------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| Math.abs(num)        | 返回num的绝对值  只处理第一个参数                            | let result = Math.abs(-1)    // 1                  |
| Math.max()           | 确定一组数值中的最大值，可以接受任意多的数值参数             | let result = Math.min(-1,3,2)  //-1                |
| Math.min()           | 确定一组数值中的最小值，可以接受任意多的数值参数             | let result = Math.min(-1,3,2)  //3                 |
|                      |                                                              |                                                    |
| Math.ceil()          | 执行向上舍入，即它总是将数值向上舍入为最接近的整数   只处理第一个参数 | let result = Math.ceil(3.4)   //4                  |
| Math.floor()         | 执行向下舍入，即它总是将数值向下舍入为最接近的整数  只处理第一个参数 | let result = Math.floor(3.6)   //3                 |
| Math.round()         | 执行标准舍入，即它总是将数值四舍五入为最接近的整数   只处理第一个参数 | let result = Math.round(3.5)  //4                  |
|                      |                                                              |                                                    |
| Math.random()        | 返回大于0小于1的一个随机数   不加参数   有参数没用           | let result = Math.random()   //0.5254465176488599  |
|                      |                                                              |                                                    |
| Math.sin(x)          | 返回x的正弦值                                                | let result = Math.sin(1)     //0.8414709848078965  |
| Math.cos(x)          | 返回x的余弦值                                                | let result = Math.cos(1)     0.5403023058681398    |
| Math.tan(x)          | 返回x的正切值                                                | let result = Math.tan(1)        1.5574077246549023 |
|                      |                                                              |                                                    |
| Math.PI              | π的值                                                        | let result = Math.PI     //3.141592653589793       |
| Math.pow(num, power) | 返回num的power次幂                                           | let result = Math.pow(2,4)   //16                  |
| Math.sqrt(num)       | 返回num的平方根                                              | let result = Math.sqrt(4)   //2                    |