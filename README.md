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

- 

### Symbol

​	ES6新增的数据类型，表示独一无二的值。能够确保对象属性使用唯一标识符。

### Null和Undefined	

```javascript
//逻辑上讲null值表示一个空对象指针，所有下面会返回“object”。
console.log(typeof null) //object
```

当变脸被声明但没有赋值就会是undefined

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

### Object

### Function

## 语句



## 变量

### var

### let

### const

### 作用域

### 内存

## Date

## Math

## RegExp

## String API

## Object API

## Array API

## Set和Map

## 异步 

### Promise

## 迭代器与生成器

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
