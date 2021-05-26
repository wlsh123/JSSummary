# JavaScript

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
  //1.concat() 
  
  //2.join() 将一个数组（或一个类数组对象）的所有元素连接成一个字符串并返回这个字符串。
   const elements = ['Fire', 'Air', 'Water'];
   console.log(elements.join(''));//"FireAirWater"
  //3.slice()
  
  //4.splice()通过删除或替换现有元素或者原地添加新的元素来修改数组,并以数组形式返回被修改的内容。此方法会改变原数组。这个方法返回值是被删除元素组成的数组
  //插入
   var myFish = ["angel", "clown", "mandarin", "sturgeon"];
   var removed = myFish.splice(2, 0, "drum");
   console.log(removed);// []
   console.log(myFish);//["angel", "clown", "drum", "mandarin", "sturgeon"]
  //删除
   var myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon'];
   var removed = myFish.splice(3, 1);
   console.log(removed);// [mandarin]
   console.log(myFish);// ["angel", "clown", "drum", "sturgeon"]
  //替换(删除后插入)
   var myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon'];
   var removed = myFish.splice(3, 1, "aaa");
   console.log(removed);// [mandarin]
   console.log(myFish);// ["angel", "clown", "drum", "sturgeon"]
  ```

- 搜素和位置方法

  ```javascript
  //1.indexOf()
  
  //2.lastIndexOf()
  
  //3.includes()
  
  //4.find() 返回数组中满足提供的测试函数的第一个元素的值。否则返回 undefined.
   const array1 = [5, 12, 8, 130, 44];
   const found = array1.find(element => element > 10);
  
  //5.findIndex() 返回数组中满足提供的测试函数的第一个元素的索引。若没有找到对应元素则返回-1。
   const foundIndex = array1.findIndex(element => element > 10);
  ```
  
- 迭代方法

  ```javascript
  //1.every() 对数组每一项都运行传入的函数，每一项都返回true，则这个方法返回true。
   [12, 5, 8, 130, 44].every(x => x >= 10);//false
  //2.some() 对数组每一项都运行传入的函数，只要有一项函数返回true，则这个方法返回true。
   [12, 5, 8, 130, 44].some(x => x >= 10);//true
  //3.forEach() 对数组每一项都运行传入的函数，没有返回值。
   [12, 5, 8, 130, 44].forEach(x => x = x+1);
  //4.map() 对数组每一项都运行传入的函数，返回值由每次函数调用的结果构成的数组。
   [12, 5, 8, 130, 44].map(x => x = x+1);
  //5.filter() 对数组每一项都运行传入的函数，函数返回true的项会组成数组之后返回.
   [12, 5, 8, 130, 44].filter(x => x >= 10);
  //6.reduce() 对数组中的每个元素执行一个由您提供的reducer函数(升序执行)，将其结果汇总为单个返回值。
   var arr = [1, 2, [3, 4]];
   arr.reduce((acc, val) => acc.concat(val), []);
  ```

- 数组“拉平”

  ```javascript
  //flat() 按照一个可指定的深度递归遍历数组，并将所有元素与遍历到的子数组中的元素合并为一个新数组返回。
   const arr1 = [0, 1, 2, [3, 4]];
   console.log(arr1.flat(1));
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


### Map(映射)

- 含义解释

  JavaScript 的对象（Object），本质上是键值对的集合（Hash 结构），但是传统上只能用字符串当作键。这给它的使用带来了很大的限制。为了解决这个问题，ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object 结构提供了“字符串—值”的对应，Map 结构提供了“值—值”的对应，是一种更完善的 Hash 结构实现。如果你需要“键值对”的数据结构，Map 比 Object 更合适。

- 基本API

  ```javascript
  //get(),set(),has(),delete(),clear(),size
   const map1 = new Map();
   map1.set('a', 'alpha');
   map1.set('b', 'beta');
   map1.set('g', 'gamma');
   console.log(map1.size);//3
   console.log(map1.get("a"))//alpha
   console.log(map1.has("a"))//true
   map1.delete("a");
   map1.clear();//清除所有成员
  ```

- 遍历方法

  ```javascript
  //1.keys() 返回键名的遍历器。
   const map = new Map([
    ['F', 'no'],
    ['T',  'yes'],
   ]);
   for (let key of map.keys()) {
    console.log(key);//F T
   }
  //2.values() 返回键值的遍历器。
   for (let value of map.values()) {
    console.log(value);//no yes
  }
  //3.entries() 返回所有成员的遍历器。
   for (let item of map.entries()) {
    console.log(item[0], item[1]);//['F', 'no'] ['T',  'yes']
  }
  //4.forEach()
  ```

- Object与Map比较

  1. 内存占用：Map大约可以比Object多存储50%的健/值对。
  2. 插入性能：涉及大量插入操作时，Map性能更优。
  3. 查找速度：设计大量查找操作时，Object性能更优。
  4. 删除性能：设计大量删除操作时，Map性能更优。

- WeakMap

  1. `WeakMap`只接受对象作为键名（`null`除外），不接受其他类型的值作为键名。
  2. `WeakMap`的键名所指向的对象，不计入垃圾回收机制。

### Set(集合)

​	Set在很多方面都像是加强的Map。它类似于数组，但是成员的值都是唯一的，没有重复的值。

- 基本API

  ```javascript
  //构造器 
   const s = new Set(); 
   const set = new Set([1, 2, 3, 4, 4]);
  //add() has() delete() clear()
   [2, 3, 5, 4, 5, 2, 2].forEach(x => s.add(x));
   s.size;
  //数组去重
   [...new Set(array)]
  //字符去重
   [...new Set('ababbc')].join('')
  ```

- 遍历方法

  ```javascript
  //keys() values() entries() forEach()
  ```

- WeakSet

### Object

- 对象解构赋值

  ```javascript
  let person = {
    name:'matt',
    age:27
  }
  let {name, age} = person;
  let {name:personName, age:personAge} = person;
  let {name, age, job='Software engineer'} = person;
  
  //嵌套解构
   let person = {
    name:'matt',
    age:27,
    job:{title:'Software engineer'}
  }
   let {job:{title}} = person
  ```

### Function

## 变量

### 变量声明

- var
- let
- const
  1. var 声明的变量属于函数作用域，let 和 const 声明的变量属于块级作用域；
  2. var 存在变量提升现象，而 let 和 const 没有此类现象；
  3. var 变量可以重复声明，而在同一个块级作用域，let 变量不能重新声明，const 变量不能修改。

### 作用域

#### [闭包](https://zhuanlan.zhihu.com/p/22486908)

### 内存

垃圾回收

- 标记清理
- 引用计数

## 语句

- 条件语句

  ```javascript
  //1.if语句
   if(condition){
     ...
   }
  //2.while语句
    while(expression){
      ...
    }
  //3.do-while语句
     do{
  			...
     }while(expression)
  ```

- 循环语句

  ```javascript
  //1.for语句
   for(initValue, expression, state){
     ...
   }
  //2.for-in语句
    for(... in ...){
      ...
    }
  //3.for-of语句
    	for(...of ...){
      ...
    }
  ```

- 分支语句

  ```javascript
  //1.switch语句
   switch(expression){
     case value1:
       statement
       continue;
     case value2:
  		 statement
       breack;
     default:
       statement
   }
  ```

## 迭代器与生成器

- Iterator(迭代器)

  它是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成遍历操作（即依次处理该数据结构的所有成员）。

  Iterator 的遍历过程是这样的。

  （1）创建一个指针对象，指向当前数据结构的起始位置。也就是说，遍历器对象本质上，就是一个指针对象。

  （2）第一次调用指针对象的`next`方法，可以将指针指向数据结构的第一个成员。

  （3）第二次调用指针对象的`next`方法，指针就指向数据结构的第二个成员。

  （4）不断调用指针对象的`next`方法，直到它指向数据结构的结束位置。

  `next`方法返回一个对象，表示当前数据成员的信息。这个对象具有`value`和`done`两个属性，`value`属性返回当前位置的成员，`done`属性是一个布尔值，表示遍历是否结束，即是否还有必要再一次调用`next`方法。

  总之，调用指针对象的`next`方法，就可以遍历事先给定的数据结构。

  原生具备 Iterator 接口的数据结构如下。

  - Array
  - Map
  - Set
  - String
  - TypedArray
  - 函数的 arguments 对象
  - NodeList 对象

- Generator(生成器)

  Generator 函数是一个普通函数，但是有两个特征。一是，`function`关键字与函数名之间有一个星号；二是，函数体内部使用`yield`表达式，定义不同的内部状态（`yield`在英语里的意思就是“产出”）。

  ```javascript
  function* helloWorldGenerator() {
    yield 'hello';
    yield 'world';
    return 'ending';
  }
  
  var hw = helloWorldGenerator();
  ```

  调用 Generator 函数后，该函数并不执行，返回的也不是函数运行结果，而是一个指向内部状态的指针对象，也就是上一章介绍的遍历器对象（Iterator Object）。

  下一步，必须调用遍历器对象的`next`方法，使得指针移向下一个状态。也就是说，每次调用`next`方法，内部指针就从函数头部或上一次停下来的地方开始执行，直到遇到下一个`yield`表达式（或`return`语句）为止。换言之，Generator 函数是分段执行的，`yield`表达式是暂停执行的标记，而`next`方法可以恢复执行。

  ```javascript
  hw.next() // { value: 'hello', done: false }
  hw.next()// { value: 'world', done: false }
  hw.next()// { value: 'ending', done: true }
  hw.next()// { value: undefined, done: true }
  ```

  总结一下，调用 Generator 函数，返回一个遍历器对象，代表 Generator 函数的内部指针。以后，每次调用遍历器对象的`next`方法，就会返回一个有着`value`和`done`两个属性的对象。`value`属性表示当前的内部状态的值，是`yield`表达式后面那个表达式的值；`done`属性是一个布尔值，表示是否遍历结束。

  - yield

  由于 Generator 函数返回的遍历器对象，只有调用`next`方法才会遍历下一个内部状态，所以其实提供了一种可以暂停执行的函数。`yield`表达式就是暂停标志。

  遍历器对象的`next`方法的运行逻辑如下。

  （1）遇到`yield`表达式，就暂停执行后面的操作，并将紧跟在`yield`后面的那个表达式的值，作为返回的对象的`value`属性值。

  （2）下一次调用`next`方法时，再继续往下执行，直到遇到下一个`yield`表达式。

  （3）如果没有再遇到新的`yield`表达式，就一直运行到函数结束，直到`return`语句为止，并将`return`语句后面的表达式的值，作为返回的对象的`value`属性值。

  （4）如果该函数没有`return`语句，则返回的对象的`value`属性值为`undefined`。

## 类

- 构造函数

  ```javascript
  class Person(){
    constructor(){
      super()
  		...
    }
  }
  ```

- 继承

  ```javascript
  class A extends react.Component(){
  	constructor(){
      super()
      ...
    }
  }
  ```

- 静态

  ```javascript
  class A extends react.Component(){
  	constructor(){
      super()
      ...
    }
    static proptype = {
      ...
    }
  }
  ```

  

## 异步 

### Promise(期约)

所谓`Promise`，简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果。从语法上说，Promise 是一个对象，从它可以获取异步操作的消息。Promise 提供统一的 API，各种异步操作都可以用同样的方法进行处理。

- 期约实例

  ```javascript
  const p = new Promise((resolve,reject)=>{
  	if(){
      resolve(value) 
       }else{
      reject(error)
    }
  })
  ```

- resolve

  ```javascript
  //作用1：不带有任何参数，返回一个Promise
   const p = Promise.resolve();
   p.then(function () {
    // ...
   });
  //作用2:参数是一个 Promise 实例，返回该实例
  //作用3:参数是一个thenable对象（thenable对象指的是具有then方法的对象），将这个对象转为 Promise 对象，然后就立即执行thenable对象的then()方法。
  let thenable = {
    then: function(resolve, reject) {
      resolve(42);
    }
  };
  
  let p1 = Promise.resolve(thenable);
  p1.then(function (value) {
    console.log(value);  // 42
  });
  //作用4:参数是其他值，返回一个新的 Promise 对象，状态为resolved。
  const p = Promise.resolve('Hello');
  
  p.then(function (s) {
    console.log(s)
  });
  // Hello
  ```

  需要注意的是，立即`resolve()`的 Promise 对象，是在本轮“事件循环”（event loop）的结束时执行，而不是在下一轮“事件循环”的开始时。

  ```javascript
  setTimeout(function () {
    console.log('three');
  }, 0);
  
  Promise.resolve().then(function () {
    console.log('two');
  });
  console.log('one');
  
  // one
  // two
  // three
  ```

- reject

  ```javascript
  //返回一个新的 Promise 实例，该实例的状态为rejected。Promise.reject()方法的参数，会原封不动地作为reject的理由，变成后续方法的参数。
  
  const p = new Promise((resolve, reject) => reject('出错了'))
  p.then(null, function (s) {
    console.log(s)
  });
  
  Promise.reject('出错了')
  .catch(e => {
    console.log(e === '出错了')
  })
  ```

  

- `then`

  `then`方法可以接受两个回调函数作为参数。第一个回调函数是`Promise`对象的状态变为`resolved`时调用，第二个回调函数是`Promise`对象的状态变为`rejected`时调用。这两个函数都是可选的，不一定要提供。它们都接受`Promise`对象传出的值作为参数。

  ```javascript
  function timeout(ms){
    return new Promise((resolve,reject)=>{
      setTimeout(resolve, ms, 'done');
    });
  }
  
  timeout(100).then((value)=>{
  	console.log(value);
  })
  ```

- catch

  ```javascript
  //用于指定发生错误时的回调函数。
  // 写法一
  const promise = new Promise(function(resolve, reject) {
    try {
      throw new Error('test');
    } catch(e) {
      reject(e);
    }
  });
  promise.catch(function(error) {
    console.log(error);
  });
  
  // 写法二
  const promise = new Promise(function(resolve, reject) {
    reject(new Error('test'));
  });
  promise.catch(function(error) {
    console.log(error);
  });
  
  //作用与then的第二个参数一致
  // bad
  promise
    .then(function(data) {
      // success
    }, function(err) {
      // error
    });
  
  // good（推荐使用，因为catch还能捕获then中的异常）
  promise
    .then(function(data) { //cb
      // success
    })
    .catch(function(err) {
      // error
    });
  ```

- finally

  ```javascript
  //在执行完then或catch指定的回调函数以后，都会执行finally方法指定的回调函数。
  promise
  .then(result => {···})
  .catch(error => {···})
  .finally(() => {···});
  ```

  

- 期约链锁

  ```javascript
  //1. then返回的也是一个Promise
  getJSON("/posts.json").then(function(json) {
    return json.post;
  }).then(function(post) {
    // ...
  });
  
  //2. catch返回的也是一个Promise
  const someAsyncThing = function() {
    return new Promise(function(resolve, reject) {
      // 下面一行会报错，因为x没有声明
      resolve(x + 2);
    });
  };
  
  someAsyncThing()
  .catch(function(error) {
    console.log('oh no', error);
  })
  .then(function() {
    console.log('carry on');
  });
  // oh no [ReferenceError: x is not defined]
  // carry on
  
  //3. finally返回的也是一个Promise
  Promise.finally.then(()=>{})
  ```

- Promise.all()

  ```javascript
  //将多个 Promise 实例，包装成一个新的 Promise 实例.
  const promises = [2, 3, 5, 7, 11, 13].map(function (id) {
    return getJSON('/post/' + id + ".json");
  });
  
  Promise.all(promises).then(function (posts) {
    ...
  }).catch(function(reason){
    ...
  });
  //所有状态都是fulfilled时，all的状态才是fulfilled；其中一个是rejected，all的状态就是rejected。
  ```

- Promise.race()

  ```javascript
  //将多个 Promise 实例，包装成一个新的 Promise 实例.
  const p = Promise.race([p1, p2, p3]);
  //只要p1、p2、p3之中有一个实例率先改变状态，p的状态就跟着改变。那个率先改变的 Promise 实例的返回值，就传递给p的回调函数。
  ```

- Promise.allSettled()

  `Promise.allSettled()`方法接受一组 Promise 实例作为参数，包装成一个新的 Promise 实例。只有等到所有这些参数实例都返回结果，不管是`fulfilled`还是`rejected`，包装实例才会结束。该方法由 [ES2020](https://github.com/tc39/proposal-promise-allSettled) 引入。

  ```javascript
  const promises = [
    fetch('/api-1'),
    fetch('/api-2'),
    fetch('/api-3'),
  ];
  
  await Promise.allSettled(promises);
  removeLoadingIndicator();
  ```

  上面代码对服务器发出三个请求，等到三个请求都结束，不管请求成功还是失败，加载的滚动图标就会消失。

  该方法返回的新的 Promise 实例，一旦结束，状态总是`fulfilled`，不会变成`rejected`。状态变成`fulfilled`后，Promise 的监听函数接收到的参数是一个数组，每个成员对应一个传入`Promise.allSettled()`的 Promise 实例。

- Promise.any()

  ES2021 引入了[`Promise.any()`方法](https://github.com/tc39/proposal-promise-any)。该方法接受一组 Promise 实例作为参数，包装成一个新的 Promise 实例返回。只要参数实例有一个变成`fulfilled`状态，包装实例就会变成`fulfilled`状态；如果所有参数实例都变成`rejected`状态，包装实例就会变成`rejected`状态。

  `Promise.any()`跟`Promise.race()`方法很像，只有一点不同，就是不会因为某个 Promise 变成`rejected`状态而结束。

  ```javascript
  const promises = [
    fetch('/endpoint-a').then(() => 'a'),
    fetch('/endpoint-b').then(() => 'b'),
    fetch('/endpoint-c').then(() => 'c'),
  ];
  try {
    const first = await Promise.any(promises);
    console.log(first);
  } catch (error) {
    console.log(error);
  }
  ```

### async(异步函数)

- 基本用法

  ```javascript
  // 函数声明
  async function foo() {}
  
  // 函数表达式
  const foo = async function () {};
  
  // 对象的方法
  let obj = { async foo() {} };
  obj.foo().then(...)
  
  // Class 的方法
  class Storage {
    constructor() {
      this.cachePromise = caches.open('avatars');
    }
  
    async getAvatar(name) {
      const cache = await this.cachePromise;
      return cache.match(`/avatars/${name}.jpg`);
    }
  }
  
  const storage = new Storage();
  storage.getAvatar('jake').then(…);
  
  // 箭头函数
  const foo = async () => {};
  ```

- 错误处理

  ```javascript
  async function f() {
    try {
      await new Promise(function (resolve, reject) {
        throw new Error('出错了');
      });
    } catch(e) {
    }
    return await('hello world');
  }
  ```

## BOM

### window对象

- 窗口位置

  ```javascript
  window.moveTo(x,y)//窗口移动到（x，y）
  window.moveBy(x,y)//窗口向右移动x像素，向上移动y像素。
  ```

- 窗口大小

  ```javascript
  //浏览器窗口中页面视口的大小
  window.innerHeight
  window.innerWidth
  
  //浏览器窗口自身的大小
  window.outerHeight
  window.outerWidth
  ```

- 视口位置

  ```javascript
  //文档相对视口滚动距离
  window.pageXoffset || window.scrollX
  window.pageYoffset || window.scrollY
  
  //scroll()、scrollTo()、scrollBy()
  window.scrollBy(0,100)//相对当前视口向下滚动100像素
  window.scrollTo(0,0)//滚动到页面左上角
  
  window.scroBy({//接收option字典，通过behavior属性告诉浏览器是否平滑滚动
    left:100,
    top:100,
    behavior:'auto'//正常滚动
  })
  window.scroTo({//接收option字典，通过behavior属性告诉浏览器是否平滑滚动
    left:100,
    top:100,
    behavior:'smooth'//平滑滚动
  })
  ```

- 打开窗口

  ```javascript
  //window.open(url,targetWin,特性字符串，true)
  
  var Win = window.open("http://www.baidu.com", "newWindow", "height=400, width=400, top=10, left=10");
  //新开一个叫“newWindow”的窗口，Win表示对这个新窗口的引用。
  
  Win.opener//指向打开它的窗口
  Win.opener == window. //true
  ```

- 定时器

  ```javascript
  //setTimeout() 指定一定时间后执行某些代码
  var timerId = setTimeout(()=>alert("hello"), 1000);
  clearTimeout(timerId);
  
  //setInterval()	指定每隔一段时间执行某些代码
  var timerId = setInterval(()=>alert("hello"), 1000);
  clearInterval(timerId);
  ```

- 对话框

  ```javascript
  //1.alter()
  //2.confirm()
  //3.prompt()
  ```

### location对象

​	这个对象即是window的属性，又是document的属性。所以window.location和document.location指向同一个对象。	

​	URL：http://foouse:barpassword@www.wrox.com:80/Will/?wq=js#contents.

| 属性              | 值                                                           | 说明                            |
| ----------------- | ------------------------------------------------------------ | ------------------------------- |
| location.hash     | '#contents'                                                  | URL散列值，如果没有就是空字符串 |
| location.host     | 'www.wrox.com:80'                                            | 服务器名及端口                  |
| location.hostname | 'www.wrox.com'                                               | 服务器名                        |
| location.href     | 'http://foouse:barpassword@www.wrox.com:80/Will/?wq=js#contents' | 完整的URL                       |
| location.pathname | '/Will/'                                                     | URL中的路径或文件名             |
| location.port     | '80'                                                         | 端口                            |
| location.protocol | 'http:'                                                      | 请求协议                        |
| location.search   | '?wq=js'                                                     | URL查询字符串                   |
| location.username | 'foouse'                                                     | 域名前指定的用户名              |
| location.password | 'barpassword'                                                | 域名前指定的密码                |
| location.origin   | 'http://www.wrox.com'                                        | URL源地址                       |

- 操作地址

  ```javascript
  //1.location.assign() 
  location.assign('http://www.baidu.com')//跳转到新页面
  
  //2.location.replace()
  location.replace('http://www.baidu.com')//跳转到新页面
  
  //3.location.reload()
  location.reload('http://www.baidu.com')//重新加载
  ```

### navigator对象

### screen对象

### history对象

- 导航

  ```javascript
  //history.go()
  history.go(-1)//后退一页
  history.go(1)//前进一页
  history.go('http://www.baidu.com')//导航到http://www.baidu.com
  
  //back()、forward()
  history.back()//后退
  history.forward()//前进
  ```

## DOM

- 操纵节点

  ```javascript
  //1.appendChild() 在节点末尾添加新节点
  //2.insertBefore() 在指定位置插入节点
  //3.replaceChild() 替换节点
  //4.removeChild() 移除节点
  //5.cloneNode() 复制节点
  ```

### document对象

document对象是HTMLDocument的实例，HTMLDocument继承Document。

```javascript
document.body//<body>元素
document.title// 文档标题
document.URL //文档URL
document.domain //域名
document.referer //来源
```

- 定位元素

  ```javascript
  //1.getElementById()
  //2.getElementsByTagName()
  //3.getElementsByName()
  //4.getElementsByClassName()
  ```

### element元素

- 元素属性

  ```javascript
  let div = document.getElementById('div');
  div.getAttribute('id')//获取id属性
  div.setAttribute('id', "mydiv")//设置id属性
  div.removeAttribute('id')//移除id属性
  ```

- 创建元素

  ```javascript
  var div = document.createElement('div')
  ```

### Selector API

- querySelector()

  ```javascript
  let body = document.querySelector("body");//取得<body>元素
  let myDiv = document.querySelector('#div'); //取得ID为‘div’的元素
  let selected = document.querySelector(".selected"); //取得类目为‘selected’的元素
  let img = document.body.queryelector('img.button'); //取得类名为‘button’的图片
  ```

- querySelectorAll()

  该方法和querySelector()一样，也接收一个用于查询的参数，但会返回所有匹配的节点。返回的是一个NodeList的静态实例。

- matches()

  ```javascript
  //接收一个CSS选择符参数，如果匹配就返回true
  if(document.body.matches('body.page1')){
     //true
     }
  ```

- 元素尺寸

  ```javascript
  offsetHeight  //元素在垂直方向上的高度
  offsetWidth  //元素在水平方向上的宽度
  
  offsetLeft //元素边框距左侧距离
  offsetTop //元素边框距上侧距离
  ```

  <img src="/Users/wanglsh/Desktop/JSSummary/src/images/元素偏移尺寸.png" style="zoom:40%;" />

- 客户端尺寸

  ```javascript
  clientHeight //内容+内边距高度
  clientWidth //内容+内边距宽度
  ```

  <img src="/Users/wanglsh/Desktop/JSSummary/src/images/元素的尺寸.png" alt="元素的尺寸" style="zoom:40%;" />

- 滚动尺寸

  ```javascript
  scrollHeight
  scrollWidth
  scrollLeft
  scrollTop
  ```

  <img src="/Users/wanglsh/Desktop/JSSummary/src/images/滚动尺寸.png" alt="滚动尺寸" style="zoom:40%;" />

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

