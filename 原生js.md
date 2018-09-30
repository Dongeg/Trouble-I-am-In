# js-fixi
js 知识复习

 ## js的数据类型
 
 五种原始数据类型 ： number string boolean null undefined
 
 一种对象类型 {function array Date}
 
 ## js隐式转换
 
 字符串转数字 typeof ('37' - 1)   // "number"
 
 数字转字符串 typeof (37 + '')   // "string"
 
 == 不判断类型
 
 === 为严格等于 两边类型不同直接返回false
 
 NaN 不等于任何值 
 
 对象和数值是按引用比较的 所以
 
 [1,2] == [1,2]  // false
 
 null == undefined // true
 
 '1' == 1 // true
 
 '0' == false // true
 
 ## 包装对象
 
 原始类型中 number boolean string 都有对应的包装对象
 
 ```js
 
var str = "abc";
undefined
var strObj = new String('abc');
undefined
str
"abc"
strObj
String {"abc"}0: "a"1: "b"2: "c"length: 3__proto__: String[[PrimitiveValue]]: "abc"
typeof strObj
"object"
typeof str
"string"


var numObj = new Number(123)
undefined
numObj
Number {123}__proto__: Number[[PrimitiveValue]]: 123


var bool = true
undefined
var boolObj = new Boolean(true)
undefined
boolObj
Boolean {true}
 
 ```
 
 string/number/boolean三个基本类型有对应包装类型，在把这几个基本类型当作对象使用时，js会创建一个对应的临时包装对象，然后进行操作，操作完毕后会消除临时对象，基本类型依然时基本类型，并无变化。
 
 ## js类型检测
 
 ### typeof 用于检测原始类型对象和function
 
 typeof 100 // 'number'
 
 ...
 
 typeof function fn(){} // "function"
 
 typeof [1,2] // "object"
 
 typeof NaN // "number"
 
 typeof null // "object"  历史遗留原因
 
 判断null可以用严格等于
 
 
 
 
 ### obj instanceof Object // 用于检测对象类型，基于原型链，判断某个对象是否由某个构造函数构造
 
 [1,2] instanceof Array  // true
 
 ### Object.prototype.toString.apply(); // 内置对象和基本类型

 Object.prototype.toString.apply([]); // "[object Array]"
 
 Object.prototype.toString.apply(function(){}); // "[object Function]"
 
 ### constructor  // 判断他的直接父构造函数
 
 ### duck type
 
 ## js表达式和运算符
 
 ### 逗号表达式
 
  var b = (1,2,4+5)
  undefined
  b
  9
  
  ### delete 运算符
  
  var obj = {x:1}
  undefined
  obj.x
  1
  delete obj.x
  true
  obj.x
  undefined
  
  ### in 
  
  window.x = 1
  1
 'x' in window
  true
  
  ### new 运算符
  
  new执行的时候发生了什么？
  
  ```js
  const a = new Foo();
  
  // 对应伪代码
  
  const o = new Object();//创建了一个新的空对象o
  o.__proto__ = Foo.prototype;//让这个o对象的` __proto__`指向构造函数的原型`prototype`
  Foo.call(o);//this指向o对象
  a = o;//将o对象赋给a对象

  ```
  1.先创建了一个新的空对象
  
  2.然后让这个空对象的__proto__指向函数的原型prototype

  3.将对象作为函数的this传进去，如果return 出来东西是对象的话就直接返回 return 的内容，没有的话就返回创建的这个对象
  
  obj.hasOwnProperty('x') // 判断 属性是他自己的，还是原型链上的
  
  ### this
  
  ### void 123 // 永远返回 undefined
  
  ## var 语句
  
  ```js
function foo(){
	var a = b = 1;
}
foo();
console.log(a); // 报错
console.log(b); // 1
  
  ```
  
  ## 异常捕获
  
  ```js
  try {
    // 尝试执行
  }
  catch(e){
    // try 中的语句报错在此处捕获异常
  }
  finally{
    // 一定会执行
  }
  ```
  
  ## 函数
  
 ```js
 
function fd (){} // 函数声明，可以在声明前调用

var fe = function(){}  // 函数表达式，不可以在声明前调用
 
 ```
 
 ## for in 语句
 
 1.顺序不确定
 
 2. enumweable 为false 时不会出现
 
 3. 原型链上有enumweable 为true时也会出现
 
 ## switch case
 
 switch(val){
  case 1: // val为1或者2执行
  case 2:
   console.log(12);
   break;
 }
 
 ## 'use strict'   // 严格模式
 
 不允许使用 with语句
 
 变量赋值前一定要声明
 
 delete 参数或函数名会报错
 
 对象字面量属性名重复会报错
 
 禁止8进制
 
 
 ## 对象
 
 创建对象的方式
 
 1.对象字面量
 
 ```js
 var obj = {
 	x:1,
	y:2,
	0:{
		z:3
	}
 }
 
 ```
 
 2. new 构造器
 
 ```js
 
function foo(){}
undefined
foo.prototype.z = 3
3
var obj = new foo();
undefined
obj.x = 1;
1
obj.x
1
obj.z
3
obj.__proto__ == foo.prototype
true
foo.__proto__ == Function.prototype
true
'z' in obj
true
obj.hasOwnProperty('z')
false
 ```
 
 3. Object.create({x:1})
 
 ```js
var obj = Object.create({x:1});
undefined
obj.x
1
obj.__proto__
{x: 1}
 ```
 
 
 
 
  
  
  
  
 
 
 
 
 
 
 
 
 
 
 
 
 
