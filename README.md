# Front-end-Knowledge-Points
本项目的目的是整理前端知识点

[知识点的思维导图](http://naotu.baidu.com/file/dbef5fd56e74b51ead825bcd83f38a56?token=2f6920a3f522cca8)

## HTML + CSS

### 选择器权重优先级

### 盒模型

### 浮动

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

在 `JavaScript` 中万物皆对象。`Null` 是所有对象的源头，`Null` 就像上帝，`Function` 和 `Object` 就是亚当和夏娃，它们通过 `prototype` 和 `constructor` 繁衍后代，`prototype` 提供基因，`constructor` 就是子宫。

* 所有的引用类型（数组、对象、函数），都具有对象特征（`Null` 除外）。
* 所有的引用类型（数组、对象、函数），都有一个浏览器提供的 `__proto__` 属性。
* 所有函数都有一个 `prototype` 属性
* 所有的引用类型（数组、对象、函数）的 `__proto__` 都指向它的构造函数的 `prototype` 属性。

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

最上层是什么 —— `Object.prototype.__proto__ === null`

### 作用域和闭包

作用域的目的是确定变量的访问权限，也就是为了避免变量污染。

首先 JavaScript 采用的是词法作用域，也就是静态作用域，即创建的时候就确定好了。

在ES6以前，JavaScript 只有全局作用域和函数作用域，没有块级作用域，不像 Java 那样，一个花括号就是一个作用域。

在ES6中 引入了 let 关键字，才有了块级作用域。

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
