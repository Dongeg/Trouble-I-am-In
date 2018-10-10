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
 
 对象和数组是按引用比较的 所以
 
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

String {"abc"}
0: "a"
1: "b"
2: "c"
length: 3
__proto__: String[[PrimitiveValue]]: "abc"


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
 
 
 ```js
 typeof 100 // 'number'
 
 ...
 
 typeof function fn(){} // "function"
 
 typeof [1,2] // "object"
 
 typeof NaN // "number"
 
 typeof null // "object"  历史遗留原因
 
 判断null可以用严格等于
 
 ```
 
 
 ### obj instanceof Object // 用于检测对象类型，基于原型链，判断某个对象是否由某个构造函数构造
 
 [1,2] instanceof Array  // true
 
 ### Object.prototype.toString.apply(); // 内置对象和基本类型
 
 ```

 Object.prototype.toString.apply([]); // "[object Array]"
 
 Object.prototype.toString.apply(function(){}); // "[object Function]"
 
 ```
 
 ### constructor  // 判断他的直接父构造函数
 
 ### duck type
 
 ## js表达式和运算符
 
 ### 逗号表达式
 
 ```
  var b = (1,2,4+5)
  undefined
  b
  9
  ```
  ### delete 运算符
  
  ```
  var obj = {x:1}
  undefined
  obj.x
  1
  delete obj.x
  true
  obj.x
  undefined
  
  ```
  ### in 
  
  ```
  window.x = 1
  1
 'x' in window
  true
  
  ```
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

  3.执行构造函数中的代码，如果return 出来东西是对象的话就直接返回 return 的内容，没有的话就返回创建的这个对象this
  
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
var obj = Object.create({x:1}); // 新创建对象的原型指向传入的参数
undefined
obj.x
1
obj.__proto__
{x: 1}
 ```
 ### 获取对象原型链
 
 ```js
// es5提供的标准方法
var a = new Object({key:123})
Object.getPrototypeOf(a)
 ```
 
 ### __proto__ protpyupe constructor 
 
 ```js
function foo(){}
undefined
var a = new foo()
undefined
a.__proto__ == foo.prototype // new出来的实例对象其 __proto__ 指向其构造函数的prototype
// a.__proto__ 和 foo.prototype 指向同一个对象，这个对象有一个 constructor 属性，其指向构造函数foo本身。所以上面的也可以这样写：
a.__proto__ == a.__proto__.constructor.prototype 
a.__proto__ === a.constructor.prototype // 这里a本身是没有constructor这个属性的，所以会访问a.__proto__.constructor
 ```
 
 ## js 属性操作
 
 ### Obeject.defineProperty()
 
 Object.defineProperty() 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性， 并返回这个对象。
 
 Object.defineProperty(obj, prop, descriptor)
 
obj        要在其上定义属性的对象。

prop       要定义或修改的属性的名称。

descriptor 将被定义或修改的属性描述符。
 
 ```js
 Object.defineProperty(obj, "key", {
  enumerable: false,// 当且仅当该属性的enumerable为true时，该属性才能够出现在对象的枚举属性中。默认为 false。
  configurable: false,  // 当且仅当该属性的 configurable 为 true 时，该属性描述符才能够被改变，同时该属性也能从对应的对象上被删除。默认为 false
  writable: false,// 当且仅当该属性的writable为true时，value才能被赋值运算符改变。默认为 false。
  value: "static"//该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。默认为 undefined。
  get : function(){
    return bValue;
  },
  set : function(newValue){
    bValue = newValue;
  },
});
 
 
 ```
 
 ### 属性读写
 
 ```js
var obj = {x:1,y:2}
undefined
obj.x
1
obj["y"]
2
for (var p in obj){
  console.log(obj[p]);//可能会遍历出原型链上的属性，顺序不确定
} 
 ```
 ```js
 for (var p in obj){
    
 }
 
 ```
 ### 读写异常
 
 ```js
 var obj = {x:1}
undefined
obj.y 
undefined
obj.y.z
Uncaught TypeError: Cannot read property 'z' of undefined
 ```

属性读写前要判断

```js
if (obj.y){
  obj.y.z = 6
}


var obj = {x:{y:1}}
undefined
var z = obj && obj.x && obj.x.y
undefined
z
1
```

### 属性删除

```
var person = {name:'deg',age:12}
undefined
delete person.age
true
person.age
undefined
```
有些属性是无法删除的，每个属性都有一个是否可配置的标签属性

```
delete Object.prototype
false
var descriptor = Object.getOwnPropertyDescriptor(Object,'prototype') // 获取对象某个属性的所有标签
undefined
descriptor.configurable // 他的是否可配置的属性为false
false
```

用 var 定义的全局和局部变量也是不可以删除的

### 检测属性是否存在

```
var cat = new Object
undefined
cat.legs = 4
4
cat.name = 'kittydkf';
"kittydkf"
'legs' in cat  
true
'toString' in cat;  // in 会向原型链上查找
true
cat.hasOwnProperty('legs')
true
cat.hasOwnProperty('toString') // 这个就不会了
false

cat.propertyIsEnumerable('legs')
true
cat.propertyIsEnumerable('toString')  // 查看属性是否可以被枚举
false
```

### getter/setter

```
var obj = {
	x:1,
	$y:null,
	get y(){
		if (this.$y){return this.$y}
		else {return '不开心呢'}
	},
	set y(val){
		this.$y = val;
	}
	
}
undefined
obj.x
1
obj.y
"不开心呢"
obj.y = '开心'
"开心"
obj.y
"开心"
```


## 数组

### 数组创建

```
var arr = [1,23,45] // 字面量

var arr2 = new Array()  // new 关键字可以省略

```

### 数组读写

```
// 增
var arr = [];
undefined
arr[0] = 0
0
arr.push(2)
2
arr[arr.length] = 3
3
arr.unshift(1)
4
arr
(4) [1, 0, 2, 3]

// 删除
delete arr[0]
true
arr
(4) [empty, 0, 2, 3]

arr.length -= 1
3
arr
(3) [empty, 0, 2]

arr.pop()
2
arr
(2) [empty, 0]

arr.shift()
undefined
arr
[0]
```

```js
//删除起始下标为1，长度为1的一个值(len设置1，如果为0，则数组不变) 
var arr = ['a','b','c','d']; 
arr.splice(1,1); 
console.log(arr); 
//['a','c','d']; 

//替换起始下标为1，长度为1的一个值为‘ttt'，len设置的1 
var arr = ['a','b','c','d']; 
arr.splice(1,1,'ttt'); 
console.log(arr);   
//['a','ttt','c','d'] 

// 添加 ---- len设置为0，item为添加的值
var arr = ['a','b','c','d']; 
arr.splice(1,0,'ttt'); 
console.log(arr);   
//['a','ttt','b','c','d']
```

### 数组上的方法

```js
// 数组转字符串
var arr = [1,2,3];
undefined
arr.join()
"1,2,3"
arr.join('_')
"1_2_3"

// 字符串重复n次
function repectString(str,n){
	return new Array(n+1).join(str);
}
undefined
repectString('我爱你',3)
"我爱你我爱你我爱你"

// 逆序
arr.reverse();
(3) [3, 2, 1]

// 排序
// 从小到大
var numList = [13,45,9,11,1,123];
undefined
numList.sort(function(a,b){
	return a-b;
})
(6) [1, 9, 11, 13, 45, 123]

// 从大到小
numList.sort(function(a,b){
	return b-a;
})
(6) [123, 45, 13, 11, 9, 1]
```

```js
var objList = [{n:11},{n:1},{n:9},{n:85},{n:36},{n:51}];
undefined
objList.sort(function(a,b){
	return a.n -b.n;
})
(6) [{…}, {…}, {…}, {…}, {…}, {…}]
0: {n: 1}
1: {n: 9}
2: {n: 11}
3: {n: 36}
4: {n: 51}
5: {n: 85}
length: 6
__proto__: Array(0)

// 数组合并
var arr = [1,2,3];
undefined
var arr2 = arr.concat([1,3],4,5)
undefined
arr2
(7) [1, 2, 3, 1, 3, 4, 5]

// 数组截取

var arr = [1,2,3,4,5,6]; // 不会对原数组进行修改
undefined
arr.slice(1,3)
(2) [2, 3]
arr
(6) [1, 2, 3, 4, 5, 6]

```
```js
//删除起始下标为1，长度为1的一个值(len设置1，如果为0，则数组不变)  会对原数组进行修改
var arr = ['a','b','c','d']; 
arr.splice(1,1); 
console.log(arr); 
//['a','c','d']; 

//替换起始下标为1，长度为1的一个值为‘ttt'，len设置的1 
var arr = ['a','b','c','d']; 
arr.splice(1,1,'ttt'); 
console.log(arr);   
//['a','ttt','c','d'] 

// 添加 ---- len设置为0，item为添加的值
var arr = ['a','b','c','d']; 
arr.splice(1,0,'ttt'); 
console.log(arr);   
//['a','ttt','b','c','d']
```


数组迭代的方式

```js
// for 循环,用于循环长度已知的数组，效率最高
for (var i = 0;i<arr.length;i++){
	console.log(arr[i])
}
// forEach() // 循环次数未知的数组
arr.forEach(function(x,index,a){
	console.log(x); // 当前元素
	console.log(index);  // 索引
	console.log(a);  // 数组
})
// for in  顺序不定，也可以变量对象属性
// 提示：for...in不应该用于迭代一个 Array，其中索引顺序很重要
for (item in arr){
	console.log(item)
}
// map // 数组映射,不修改原数组

arr.map(function(x){
	return x+10;
})
(6) [11, 12, 13, 14, 15, 16]

// filter  // 过滤出符合条件的元素
arr.filter(function(x,i){
	return x > 3
})
(3) [4, 5, 6]

// 数组判断

// 数组中的每个元素都符合某个条件返回true,否则返回false
arr.every(function(x,i){
	return x > 3
})
false


// 数组中的只要有一个元素都符合某个条件返回true,否则返回false
arr.some(function(x,i){
	return x > 3
})
true

// reduce reduceRight,不修改原数组
// reduceRight 从右向左
//reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。对空数组是不会执行回调函数的。

```js
// 求和
var sum = arr.reduce(function(x,y){
	return x+y; // 结过作为参数传入下一次迭代中的x
})
undefined
sum
21

// 找出最大值
```
var max = arr.reduce(function(x,y){
	return x>y?x:y;
})
undefined
max
6

```

// for of



```
//indexOf() 方法可返回某个指定的字符串值在字符串中首次出现的位置.找不到返回-1；

// 数组去重

```js
function fn(arr){
	var result = [];
	for (var i = 0;i<arr.length;i++){
		if(result.indexOf(arr[i]) == -1){
			result.push(arr[i])
		}
	}
	return result;
}
undefined
fn(arr)
(6) [1, 2, 3, 4, 5, 6]
```
// 判断是否为数组

```js
Array.isArray([])
true

[] instanceof Array
true

({}).toString.apply([])
"[object Array]"

[].constructor === Array
true

```


## 函数

### 创建方式

```
// 函数声明

// 会变量提升

function add(){

}

// 函数表达式

// 变量的值（函数体）不会提升

var add = function(){
}

// 立即执行函数表达式
(function(){
	// do sth
})()

return function(){

}
// 命名式函数表达式
var add = function foo (a,b){

}

// 函数构造器
var func = new Function('a','b','console.log(a+b)');
undefined
func(1,2)
3
undefined

```

### this

全局作用域下this指向window

函数中this指向调用它的对象

构造函数中的 this 指向构造函数的prototype

改变this的指向 call/apply/bind

call和apply都是对函数的直接调用，而bind方法返回的仍然是一个函数，因此后面还需要调用

```js
function add(c,d){
	return this.a +this.b+c+d;
}
undefined
var o = {a:1,b:3}
undefined
add.call(o,3,4)
11
add.apply(o,[3,4])
11
var g = add.bind(o,6) //绑定一次，多次执行,第一个参数传null或者undefined，则指向window，new的时候会失效
g(8)
18
```

### arguments

```js
function foo(x,y,z){
	return {
		l:arguments.length, // 实参个数
		0:arguments[0]    // 第一个参数
	}
}
undefined
foo(1,2)
{0: 1, l: 2}
foo.length  // 形参个数
3
foo.name   // 函数名
"foo"
```

bind 可以做函数柯里化

柯里化是把接受多个参数的函数变换成接受一个单一参数（最初函数的第一个参数）的函数，并且返回接受余下的参数而且返回结果的新函数的技术

```js
function foo(a,b,c,d,e,f,g){
	console.log(a,b,c,d,e,f,g)
}
undefined
var currying = foo.bind(null,'q','w','e','r','t','y');
undefined
currying('我爱你')
q w e r t y 我爱你
```

## 闭包 

```html
<!-- 点击弹出索引 -->
<button class="btn">btn</button>
<button class="btn">btn</button>
<button class="btn">btn</button>
<button class="btn">btn</button>
<button class="btn">btn</button>
<button class="btn">btn</button>
<button class="btn">btn</button>
<script>
	var btns = document.querySelectorAll('.btn');
	
	// 绑定索引
	for(var i = 0;i<btns.length;i++){
		btns[i].index = i
		btns[i].onclick=function(){
			alert(this.index);
		}
	}
	// 闭包
					  				  
	for(var i = 0;i<btns.length;i++){
		!function(i){
			btns[i].onclick=function(){
			alert(i);
		}
		}(i)
	}		
</script>


```

// 创建局部作用域

```js

(function(){
var $x = 1;
var local = {};
local.getx =function(){
	return $x;
}
window.data = local;
})() 
console.log(data.getx());

```

## js作用域

全局作用域

函数作用域

eval作用域

## oop

```js
      function Person (name,age){
          this.name = name;
          this.age = age;
      }
      Person.prototype.hi = function(){
          console.log(' i am' + this.name +this.age);
      }
      Person.prototype.EYE = 2; 
      Person.prototype.walk = function(){
        console.log(this.name + 'is working');
      } 
      function Student(name,age,className){
          Person.call(this,name,age);
          this.className = className;
      }
      // 如果直接Student.prototype = Person.prototype;则如果在 Student.prototype上修改Person.prototype也会受影响
      Student.prototype = Object.create(Person.prototype); 
      Student.prototype.constructor = Student;
      //重写原型链上的hi方法
      Student.prototype.hi = function(){
        console.log(' i am' + this.name +this.age + this.className);
      }
      Student.prototype.learn = function(){
        console.log(this.name +'is learning');
      }

      var xiaoming = new Student('xiaoming',18,'nb');
      xiaoming.hi();
      xiaoming.EYE;
      xiaoming.walk();
      xiaoming.learn();

```

## 模拟重载

```js
      function Person (){
          var args = arguments;
          if (typeof args[0] === 'object' && args[0]){  // 假定只传一个参数，且类型为对象且不为null;
            if (args[0].name){
                this.name = args[0].name;
            }
            if (args[0].age){
                this.age = args[0].age;
            }
          }
          else if (typeof args[0] === 'string'){
            if (args[0]){
                this.name = args[0];
            }
            if (args[1]){
                this.age = args[1];
            }
          }
      }
      Person.prototype.printMsg = function(){
          console.log( this.name + ' ' + this.age )
      }

      var p1 = new Person('xiaoming',18);
      p1.printMsg(); // xiaoming 18
      var p1 = new Person({name:'xiaoming',age:18});
      p1.printMsg(); // xiaoming 18

```

### 链式调用

```js

      function classManager(){};
      classManager.prototype.addClass = function (str){
          console.log(str);
          return this;  // 通过返回this实现
      }
      var manager = new classManager();
      manager.addClass('classA').addClass('classB').addClass('classC');
      
      classA
      classB
      classC
```




















 
 
 
 
 
  
  
  
  
 
 
 
 
 
 
 
 
 
 
 
 
 
