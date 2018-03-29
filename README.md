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

![](https://raw.githubusercontent.com/goldEli/Front-end-Knowledge-Points/master/imgs/2.png)

如果子 div 设置了 float，会导致父 div 出现坍塌。因为设置 float 会让子 div 脱离文档流

**包裹性**

![](https://raw.githubusercontent.com/goldEli/Front-end-Knowledge-Points/master/imgs/1.png)

div 属于块级元素，如果不设置宽度，会撑满整个宽度，当设置 `float:left` 时，会让 div 包裹文字。这就印证了它的设计初衷，让文字环绕图片，如果没有包裹性，它就无法紧贴文字。

**清空空格**

当几个图片在一排显示时，有留有空格。设置 float 让图片脱离文档流，既然都脱离文档流了，那么什么空格换行都跟他没关系了。

**清除浮动**

```
.clearfix:after {
    content: '';
    display: table;
    clear: both;
}
.clearfix {
    *zoom: 1; /* 兼容 IE 低版本 */
}
```

### 定位

可选属性 `static/relative/absolute/fixed`

**absolute**

* 脱离文档流
* 包裹性
* 跟随性
* 悬浮页面上方，挡住下面的内容

### flex布局

基本使用：

```
<style type="text/css">
    .container {
      display: flex;
    }
    .item {
        border: 1px solid #000;
        flex: 1;
    }
</style> 
<div class="container"> 
	<div class="item">aaa</div> 
	<div class="item" style="flex: 2">bbb</div> 
	<div class="item">ccc</div> 
	<div class="item">ddd</div> 
</div>
```
![](https://user-gold-cdn.xitu.io/2018/2/23/161c1066b5766be2?imageView2/0/w/1280/h/960/ignore-error/1)

### 如何实现居中对齐

**水平居中**

* inline 居中

```
text-aligin: center 	
```
* block 居中

```
.container {
    text-align: center; 
}
.item {
    width: 1000px;
    margin: auto; 
}
```

* 绝对定位居中

```
.container {
    width: 500px;
    height: 100px;
    position: relative; 
}
.item {
    width: 100px;
    height: 100px; 
    position: absolute;
    left: 50%;
    margin-left: -50px
}
```
**垂直居中**

* inline 居中

```
.container {
   height: 50px;
   line-height: 50px;
}
```

* block 居中

可以用绝对定位居中（同上），也可以用 `margin:auto`，不需要提前知道尺寸，且通用性好。

```
.container { position: relative; height: 300px; } 
.item { 
	width: 100px; 
	height: 50px; 
	position: absolute; 
	left: 0; 
	top: 0; 
	right: 0; 
	bottom: 0; 
	margin: auto; 
}
```


### 语义化

让人和机器更容易读懂代码

比如 h1 p header strong 这些标签，方便搜索引擎爬网页

### CSS动画

```
@keyframes testAnimation { 
    0% {background: red; left:0; top:0;} 
    25% {background: yellow; left:200px; top:0;} 
    50% {background: blue; left:200px; top:200px;} 
    75% {background: green; left:0; top:200px;} 
    100% {background: red; left:0; top:0;} 
}
div {
    width: 100px;
    height: 50px;
    position: absolute;

    animation-name: testAnimation;
    animation-duration: 5s;
}
```

### 重绘和回流

重绘：指的是浏览器重新绘制样式，比如颜色，背景等，不会脱离文本流。

回流：会脱离文本流，当元素的大小，或者属性发生改变，会导致浏览器重新渲染部分或者全部文档

相比之下，回流比重绘更消耗性能。编码时，要尽量避免回流。

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
