# Front-end-Knowledge-Points
本项目的目的是整理前端知识点

[知识点的思维导图](http://naotu.baidu.com/file/dbef5fd56e74b51ead825bcd83f38a56?token=2f6920a3f522cca8)

## HTML + CSS

### 选择器权重优先级

* 内联样式：如 `style=""` 权重为1000
* ID选择器： 如 `#box` 权重为100
* 类、伪类和属性选择器： 如 `.box` `:hover` `[attribute]` 权重为10
* 元素选择器和伪元素选择器：如 `p` `div` 权重为1
* 通用选择器（*）、子选择器（<）、相邻同胞选择器（+）权重为0

**权重值越大优先级越高，相同权重遵循后定义的覆盖先定义的**

### 盒模型

三个核心：`padding`、`border`、`margin`

盒子的宽度：内容宽度 + `padding`宽度 + `border`宽度 + `margin`宽度。改变任何一个都会改变整个宽度。

如果设置了`box-sizing:border-box`，那么设置 `width:100px`时，这`100px` 包含了（内容 + `padding`宽度 + `border`宽度）

#### 纵向 margin 重叠

当两个 `div` 的 `margin` 为 20px，那么两个div的纵向的距离不是 40px，而是20px，因为纵向的 `margin` 会重叠。如果一个的比另一个的 margin 大，那么遵循大的吃小的原则。

### 浮动

float 的设计初衷是为了图片的环绕效果，当图片设置了 `float:left` 文字会环绕图片周围。

#### float + div

人们发现 float + div 可以解决类似 table 的布局，所以 float 现在常常用来布局。

**破坏性**

如果子 div 设置了 float，会导致父 div 出现坍塌。因为设置 float 会让子 div 脱离文档流

**包裹性**




### 定位

### flex布局

### 如何实现居中对齐

### 语义化

### CSS动画

### 重绘和回流

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

### <a herf="#scope">作用域</a>

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

## 浏览器

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
