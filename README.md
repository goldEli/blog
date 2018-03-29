# Front-end-Knowledge-Points
本项目的目的是整理前端知识点

[知识点的思维导图](http://naotu.baidu.com/file/dbef5fd56e74b51ead825bcd83f38a56?token=2f6920a3f522cca8)

## [HTML + CSS](https://github.com/goldEli/Front-end-Knowledge-Points/issues/2)

## JavaScript

### 变量类型

基本类型：`Null` `Undefined` `String` `Number` `Boolean` `Symbol` 

引用类型：`Object` `Function`

判断类型的方法：type of

判断实例与构造函数依赖的方法：instanceof

### 原型和原型链

在 JavaScript 中万物皆对象。Null 是所有对象的源头，Null就像上帝，Function 和 Object 就是亚当和夏娃，它们通过 prototype 和 constructor 繁衍后代，prototype 提供基因，constructor 就是子宫。

* 所有的引用类型（数组、对象、函数），都具有对象特征（Null 除外）。
* 所有的引用类型（数组、对象、函数），都有一个浏览器提供的 __proto__ 属性。
* 所有函数都有一个 prototype 属性
* 所有的引用类型（数组、对象、函数）的 __proto__ 都指向它的构造函数的 prototype 属性。

用代码来描述：

```
// 对象可扩展
var obj = {};
obj.b = 1
var arr = [];
arr.b = 1
function fn() {}
fn.b = 1 

// 判断对象中是否存在该属性
obj.hasOwnProperty('b') === true

// __proto__
console.log(obj.__proto__)
console.log(arr.__proto__)
console.log(fn.__proto__)

// 只有函数有 prototype
console.log(obj.prototype) // undefined
console.log(arr.prototype)	// undefined
console.log(fn.prototype)

// 应用类型的 __proto__ 属性指向它构造函数的 prototype 属性
console.log(fn.__proto__ === fn.constructor.prototype)                
console.log(fn.__proto__ === Function.prototype)                
console.log(arr.__proto__ === Array.prototype)                
console.log(obj.__proto__ === Object.prototype) 
```

当对象 `obj` 在访问属性的时候，会在自身属性中寻找，如果自身没有，就会通过 `obj.__proto__` （即构造函数的 `prototype`）中去寻找。如果还没有就会继续通过 `obj.__proto__.__proto__` 中去寻找，一直向上寻找，就形成了**原型链**。如果在最上层也没找到，就会返回 `undefined`。

最上层是什么 —— Object.prototype.__proto__ === null

### 作用域

#### 作用域

作用域的目的是确定变量的访问权限，也就是为了避免变量污染。

首先 JavaScript 采用的是词法作用域，也就是静态作用域，即创建的时候就确定好了。

在ES6以前，JavaScript 只有全局作用域和函数作用域，没有块级作用域，不像 Java 那样，一个花括号就是一个作用域。

在ES6中 引入了 let 关键字，才有了块级作用域。

#### 作用域链

当变量查找时，会从当前上下文中的变量对象中查找，如果没有，会从父级上下文的变量对象中查找，直到找到全局的变量。由多个执行上下文的变量对象构成的链表就叫作用域链

#### 闭包

闭包指的是，有权限访问访问其他作用域中变量的函数。

理解闭包核心：**JavaScript的函数作用域是在函数创建的时候定义的，而不是在执行的时候创建的**

看下面的例子：

```
function out() {
	var name = "js"
	return function inner(){
		console.log(name)
	}
}
var fn = out() // fn 引用了 out 的作用域
fn() // 当 fn 执行的时候就可以访问到 out 的作用域中的 name 变量
```

out 执行时创建执行上下文，out 执行完后上下文被销毁了，为什么还能访问到呢？先来看看 JavaScript 的垃圾回收机制。

##### 垃圾回收机制

**引用计数**

当声明一个变量，将一个引用类型赋值给该变量，则当前引用次数为1，如果同一个值赋给另一个变量，则引用次数加1。相反，如果拥有该值的变量拥有了其他值则减1，当值的引用次数为0时，垃圾回收期下次运行时，就会回收。

下面这个例子：

```
function func() {
	var a = new Object()
	var b = new Object()
	
	a.someOtherObject = b
	b.otherObject = a
}
// 这两个值引用次数都为2，永远不会回收
```
 	
**标记清除**
	
当函数中声明一个变量，则标记这个变量为“进入环境”，只要进入相应的环境你就可以访问到它。当变量离开环境时，则将其标记会“离开环境”

### 异步

### ES6/7常用特性

## web-api

### BOM

浏览器提供的一些接口，比如 `location`、`screen`、`navigator`、 `history`。

### DOM

起初使用 xml 来描述页面结构，为了标准化，推出了 html，当浏览器通过 url 请求服务器，服务器返回 html 给浏览器，浏览器和 JavaScript 都不认识 html，所以浏览器会把 html 转换成 DOM，DOM 是一个树结构

**获取 DOM**

```
// 通过 id 获取
var dom = document.getElementById('box')

// 
```

**property 和 attribute的区别**

* property

DOM 节点就是一个 js 对象，比如一个 p 节点，可以拥有 `class` `style` 等属性

* attribute

属于 html 的属性，需要通过 getAttribute 和 setAttribute 来操作属性，改操作会造成重绘和重排，所以尽量避免频繁操作。

## Framework

### React

### Vue

### Angular

## 打包工具

## 算法

## 参考
[Web 前端面试指南与高频考题解析](https://juejin.im/book/5a8f9ddcf265da4e9f6fb959)
[冴羽博客](https://github.com/mqyqingfeng/Blog)
[实现compose的五种思路](https://segmentfault.com/a/1190000011447164)
