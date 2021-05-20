# JSSummary

<!--备注：该仓库主要是记录平时学习js的相关知识点-->

[TOC]

## 数据类型

<!--基本数据类型-->

### Number

- 进制转换

  十转二：十进制数除2取余法，即十进制数除2，余数为权位上的数，得到的商值继续除2，依此步骤继续向下运算直到商为0为止。

  ![](https://exp-picture.cdn.bcebos.com/19587f20a7cd0c6e25e65907fed7997bbaf4dda8.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fquality%2Cq_80)

  二转十：把二进制数按权展开、相加即得十进制数。

  ![](https://exp-picture.cdn.bcebos.com/03f26bd7997bbbf4394c296e5549610f8a56d6a8.jpg?x-bce-process=image%2Fresize%2Cm_lfit%2Cw_500%2Climit_1%2Fquality%2Cq_80)

  <!--其他的进制转换关系可以看./src/images-->
  
- 浮点数与整数

  浮点数在存储的时候占用的内存空间是整数的两倍。所以能转换成整数就存储整数（10.0会当成10处理）。

  ```javascript
  //ES5
  parseInt(10.1) //10
  parseFloat('123.45#')//123.45
  //ES6 将全局方法parseInt()和parseFloat()，移植到Number对象上面，行为完全保持不变。
  Number.parseInt('12.34') //12
  Number.parseFloat('123.45#') //123.45
  ```

  ```javascript
  Number.isInteger('') //用来判断一个数值是否为整数。
  ```

- 最大值和最小值

  ```javascript
  Number.MAX_VALUE Number.MIN_VALUE 
  //ES6 在Number对象上面，新增一个极小的常量Number.EPSILON。
  Number.EPSILON//如果两个数之间的差值小于这个值就可以判断这两个值相等。
  Number.isFinite()//可以判断一个值是否有限
  ```

- NaN

  NaN用来表示本来应该返回数值的操作失败了（5/0）。

  ```javascript
  Number.isNaN()//如果参数类型不是NaN，Number.isNaN一律返回false。
  ```

### String

​	转义字符：\n、\t、\0	

​	字符串是不可变的，一旦创建，要修改值必须要先销毁原始的字符串。	

​	v.toString()可以把一个值转换成字符串。

​	<!--扩展：JSON.stringify()可以把接口返回的JSON对象转换成json字符串。-->

​	模版字符串：`Hello ${name}!`

- 字符转换

  ```javascript
  var x = new String("Hello world");
  console.log(x.toString())//"Hello world"
  ```

- 字符串拼接

  ```javascript
  //concat() 将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。
   str1.concat(str2,str3);
  ```

- 字符串查找

  ```javascript
  //1.indexOf() 从字符串对象中返回首个被发现的给定值的索引值，如果没有找到则返回-1。
   const str = 'hello world ni hao world';
   str.indexOf('o');//4
  
  //2.lastIndexOf() 从字符串对象中返回最后一个被发现的给定值的索引值，如果没有找到则返回-1。
   str.lastIndexOf('o')//20
  
  //3.startsWith() 判断当前字符串是否以另外一个给定的子字符串开头，并根据判断结果返回 true 或 false。
   str.startsWith('hello'); //true
  
  //4.endsWith() 判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 true 或 false。
   str.endsWith('shi jie');//true
  
  //5.includes() 返回布尔值，表示是否找到了参数字符串。
   str.includes('')
  ```

- 字符填充

  ```javascript
  //1.padStart() 在当前字符串头部填充指定的字符串， 直到达到指定的长度。 返回一个新的字符串。
   var str = "hello";
   console.log(str1.padStart(10, '*')); //"*****hello"
  //2.padEnd() 在当前字符串尾部填充指定的字符串， 直到达到指定的长度。 返回一个新的字符串。
   console.log(str1.padEnd(10, "#"));//"hello#####"
  ```

- 大小写转换

  ```javascript
  //1.toLocaleUpperCase()
  //2.toUpperCase()
  //3.toLowerCase()
  //4.toLocaleLowerCase()
  ```

- 去除空格

  ```javascript
  //1.trim()
  
  //2.trimStart()
  
  //3.trimEnd()
  ```

- 字符串裁剪

  ```javascript
  //1.slice() 提取某个字符串的一部分，并返回一个新的字符串，且不会改动原字符串。
   const str1 = "hello world ni hao"
   
  //2.split() 使用指定的分隔符字符串将一个String对象分割成子字符串数组，以一个指定的分割字串来决定每个拆分的位置。 
   console.log(str1.split(''));//["hello", "world", "ni", "hao"]
  
  //3.substring() 返回一个字符串在开始索引到结束索引之间的一个子集, 或从开始索引直到字符串的末尾的一个子集。
   console.log(str1.substring(0,5))//hello
  ```

  

### Symbol

​	ES6新增的数据类型，表示独一无二的值。能够确保对象属性使用唯一标识符。

### Null和Undefined	

```javascript
//逻辑上讲null值表示一个空对象指针，所有下面会返回“object”。
console.log(typeof null) //object
```

当变量被声明但没有赋值就会是undefined

### Boolean

​	只有两个字面量true、false。	

| 数据类型 | true       | false         |
| -------- | ---------- | ------------- |
| Boolean  | true       | false         |
| String   | 非空字符串 | ‘’ ‘’（空串） |
| Number   | 非零数值   | 0， NaN       |
| Object   | 任意对象   | null          |

<!--引用数据类型-->

### Array

- 创建数组

  ```javascript
  //1.构造器
   let colors = new Array();
  //2.数组字面量
   let values = [1,2];
  //3.ES6静态方法
   Array.from('foo')//从一个类似数组或可迭代对象创建一个新的，浅拷贝的数组实例。
   Array.of(1,2,3)//创建一个具有可变数量参数的新数组实例
  ```

- 数组空位

  ```javascript
  //可以创建空位数组
  const a = [1,,,,5];
  a.map()//跳过空位
  a.join()//空位看作空字符串
  ```

- 数组索引

  ```javascript
  //length不是只读，可以修改它实现增删元素
  let s = [1,2,3];
  s.length = 2;
  s[2] //undefined
  s.length = 4;
  s[3] //undefined
  ```

- 检测数组

  ```javascript
  //1.instanceof
   value instanceof Array;
  //2.isArray() -推荐使用
   Array.isArray(value)
  ```

- 迭代器方法

  ```javascript
  //1.Array.keys()
  const array1 = ['a', 'b', 'c'];
  const iterator = array1.keys();//返回由数组索引组成的迭代器
  for (const key of iterator) {
    console.log(key);//[0,1,2]
  }
  
  //2.Array.values()
  const iterator = array1.values();//返回由数组元素组成的迭代器
  for (const key of iterator) {
    console.log(key);//[a,b,c]
  }
  
  //3.Array.entries()
  const iterator = array1.entries();//返回由数组索引和值组成的迭代器
  for (const key of iterator) {
    console.log(key);//[[0,a],[1,b],[2,c]]
  }
  ```

- 数组复制

  ```javascript
  //copyWithin 浅复制数组的一部分到同一数组中的另一个位置，并返回它，不会改变原数组的长度。
  const array1 = ['a', 'b', 'c', 'd', 'e'];
  console.log(array1.copyWithin(1, 2, 4));//[a,c,d,d,e]
  ```

- 数组填充

  ```javascript
  //fill 用一个固定值填充一个数组中从起始索引到终止索引内的全部元素。(不包括终止索引)
  const array1 = [1, 2, 3, 4];
  console.log(array1.fill("*", 2, 4));//[1,2,"*","*"]
  ```

- 数组转换

  ```javascript
  /*这三个方法所有对象都有，Array、Number、String、Date...*/
  //1.toLocaleString()
   返回一个字符串表示数组中的元素。
  //2.toString()
   const array1 = [1, 2, 'a', '1a'];
   console.log(array1.toString());//返数组元素组成的字符串（中间会有‘,’）
  //3.valueOf()
  ```

- 栈方法

  ```javascript
  //push() 将一个或多个元素添加到数组的末尾，并返回数组的新长度。
   const animals = ['pigs', 'goats', 'sheep'];
   const count = animals.push('cows');
   console.log(count+animals);
  //pop() 从数组中删除最后一个元素，并返回该元素的值。
   const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];
   console.log(plants.pop());
  ```

- 队列方法

  ```javascript
  //unshift() 将一个或多个元素添加到数组的开头，并返回该数组的新长度
   const animals = ['pigs', 'goats', 'sheep'];
   const count = animals.unshift('cows');
   console.log(count+animals);
  //shift() 从数组中删除第一个元素，并返回该元素的值
   const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];
   console.log(plants.shift());
  ```

- 排序方法

  ```javascript
  //reverse() 反转数组，改变数组并返回
   const array1 = ['one', 'two', 'three'];
   const reversed = array1.reverse();
   console.log('reversed:', reversed);
  //sort([compareFunction]) 比较函数返回正值就换位置，返回负值就不换位置
   var numbers = [4, 2, 5, 1, 3];
   numbers.sort((a, b) => a - b)//增序
  ```

- 操作方法

  ```javascript
  
  ```

- 扩展运算符

  ```javascript
  /*ES6中的三个点 ... 有两个名字:rest参数和扩展运算符.
  当用在函数定义时的形参前面时,称为rest参数,当函数调用时,用于接收不确定的参数.
  当与解构赋值组合使用时,称为rest参数,用于接收剩余的值,存储在数组中.
  当用在字符串或数组前面时称为扩展运算符,将数组或字符串进行拆解.
  */
  
  function sumRest (...m) {
  	var total = 0; 
  	for(var i of m){
  	    total += i;
  	}
  	return total;
  }
  console.log(sumRest(1,2,3));//6
  
  var array = [1,2,3,4,5];
  console.log(...array);//1 2 3 4 5
  var str = "String";
  console.log(...str);//S t r i n g
  ```

  

### Object

### Function

## 迭代器与生成器

### 数据结构

## 语句



## 变量

### var

### let

### const

### 作用域

### 原型、原型链

### 内存

## Date

## Math

## RegExp

## Set和Map

## 异步 

### Promise

## BOM

## DOM

## 事件

## 网络请求

### XHR

### jQuery

### AJAX

### axios

## 代理

## 客户端存储

### cookie

### Web Storage

#### session

#### localStorage

## Module
