# React

> [Learn Enough React For The Interview](https://medium.com/bb-tutorials-and-thoughts/learn-enough-react-for-the-interview-f460a2fa3aeb)

React is one of the most popular javascript libraries and it's going to be more popular in 2019 and beyond. React is released in 2013 and it gained a lot of popularity over the years.  It's a declarative, component-based and efficient javascript library for building user interfaces.

## What is declarative programming?

Declarative programming is a programming paradigm which focuse on what you do rather than how you do. It expresses the logic without explicitly defining the steps. What it means is we need declare the component depending on the computation of the log. It doesn't describe the control flow steps. Examples of declarative programming are HTML, SQL, JSX, etc.

## Declarative programming vs Imperative programming.

Declarative programming is written in such a way that it describes what should be done. Imperative programming describes how to do it. In declarative programming, you let the compiler decide how to do the things. Declarative programming is easy to reading because of the code itself describe what is it doing.

Here is an example where we want to increment each element in an Array. with declarative, we are using map function and let the compiler do the rest. with imperative, we are writing all the control flow steps.

```javascript
const numbers = [1,2,3,4,5,6]

// declarative programming
const doubleWithDec = numbers.map(number => number*2)

console.log(doubleWithDec)


// imperative programming
const doubleWithImp = []
for (let i = 0; i < numbers.length; ++i) {
  const numberDouble = numbers[i] * 2
  doubleWithImp.push(numberDouble)
}

console.log(doubleWithImp)
```
## What is functional programming?

Functional programming is a part of declarative programming. Functions in javascript are first class citizen which means functions are data and you can save, retrieve, and pass those functions throughout your application. 

There are some core concepts of functional programming:

* Immutability
* Prue function
* Data transformation
* Higher-order function
* Recursion
* Composition

### Immutability

Immutability means unchangeable. In functional programming, you can't change the data and it never changes. if you want to mutate or change the data, you have to copy data and change the copied version and uses it.

### Prue functions

Prue functions are the functions which always take one or more arguments and computes on arguments and return data or functions. It doesn't have the side effect such as set a global state, changing application state and it always treats arguments as immutable data.

### Higher-order functions

Higher-order functions are the functions which take functions as arguments or return function or sometimes they do both. The higher-order functions can manipulate other functions.

`Array.map`, `Array.filter` and `Array.reduce` are higher-order functions since they take functions as arguments.

### Recursion

Recursion is a technique where the functions can call itself until the condition is met. It's better to use recursion instead of the loop whenever possible. You should be careful to use this since browsers can't handle too much recursion and throw errors. 

### Composition

In React, we divide the features into reusable pure functions and we have to put them together to make it product eventually. we combine all those smaller functions and eventually, you would get an application. It called composition. 

There are a lot of methods or implementations to implement composition. one of we familiar method from javascript is chaining,  Chaining invokes a function on the return value of the previous function with the dot notation.

In React, we use a different method other than chaining because of it hard to do chaining more functions like 30. The goal here is to combine all smaller functions to generate a higher order function.

## What is React?

React is a UI Library for building efficient user interfaces. It is a lightweight library which makes it popular. It follows the component design pattern, declarative programming paradigm,  and functional programming concepts to make front end apps efficient. It uses virtual DOM to efficiently manipulates DOM. It follows the one-way data flow from higher order components to lower order components.

## How does it differ from Angular?

Angular is a full blown MVC framework and comes with a lot of opinionated features such as servers, templates, directives, resolvers, etc. React is a very lightweight UI library which focuses only on the view part of MVC. Angular follows two-directional data flow whereas React follows uni-directional data flow which is top to down approach. React gives a lot of freedom for developers when it comes to developing features. For examples, the way you call API, routing, etc. you don't have to include router library unless you need it in your project. 

## What is Virtual DOM and how it works?

React use virtual DOM to update real DOM which makes it efficient and faster. Let's discuss those in detail.

* **What is Virtual DOM**

The browser follows HTML instructions to document object model or DOM. All the elements became DOM elements when the browser load HTML and renders the user interface.

DOM is a hierarchy of elements starting with the root element. For example, look at the following HTML: 

```HTML
<div>
    <div>
        <h1>This is heading</h1>
        <p>this is paragraph</p>
        <div>
            <p>This is just a paragraon</p>
        </div>
    </div>
    <div>
        <h1>This is heading</h1>
        <p>this is paragraph</p>
        <div>
            <p>This is just a paragraon</p>
        </div>
    </div>
    <div>
        <h1>This is heading</h1>
        <p>this is paragraph</p>
        <div>
            <p>This is just a paragraon</p>
        </div>
    </div>
</div>
```

When you load this HTML in the browser, all the HTML elements translate DOM elements like blew.

![](https://cdn-images-1.medium.com/max/1600/1*yosvJviLqQ023jO8Jn48hQ.png)

When it comes to SPA application. you load the **index.html** for the first time and updated data or another HTML in that **index.html**. As users navigate through the site, we update the same **index.html** with the new content. Every time DOM changes, the browser recalculates the CSS, do layout, and repaint the web page.

React use Virtual DOM to construct DOM efficiently, which makes it a very complicated and time-consuming task of DOM manipulation easier for us. React abstracts away all this from developers to build the efficient UI with the help of Virtual DOM.
 

