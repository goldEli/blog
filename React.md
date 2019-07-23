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
 
* **How dose Virtual DOM works?**

Virtual DOM is nothing but javaScirpt object representation of real DOM. Updating javaScript object is easier and faster when compared with updating the real DOM. With this in mind, let's see how it works.

React keeps the entire copy of DOM as a virtual DOM.

![](https://miro.medium.com/max/1400/1*rapZW61W1dr0cEpOXqJaEA.png)

Whenever there is an update comes, It miantains tow virtual DOMs to compare the previous state and current state and figures out what objects have ben changed. For instance, paragraph text changed to change.

![](https://miro.medium.com/max/1400/1*xVfZDNDw7ufCmGDXlhQLdw.png)

Now It finds out the changes by comparing two virtual DOMs and sends throse updates to real DOM.

![](https://miro.medium.com/max/1400/1*chGf5cb0BlZrRX9wEulKjA.png)

Once real DOM updates, the UI updates as well.

![](https://miro.medium.com/max/1400/1*l_Q6PS3EZodhJdrOirAw7w.png)

## What is JSX?

JSX is a syntax extension to javascript. It's a template language with the full power of javascirpt. It produces React elements which will be rendered in the DOM. React recommands use JSX for components. In JSX, we combine both HTML and Javascript and produces React elements which can be rendered in the DOM.

Here is an example of JSX, we can see how we are combining javascript and HTML. If there is any dynamic variable included in HTML, we should use the expression language **`{}`**

````jsx
function App() {
  const content = "Hello World!"
  return (
    <div>{content}</div>
  )
}
````

## Component and Different Types

Everything is a component in React. We usually break up the entire logic of the application into small individual pieces. We call each individual piece as a component. In general, A component is a javascript function which takes the input, process it and return React element which renders in the UI.

There are different types of components, let's see throse in detail.

### Functional / Stateless / Presentational Components

A functional or stateless component is pure function which takes props or no props and returns React element. There are pure functions which don't have any side effects. Those components don't have state and lifecycle methods。Here is an example.

```jsx
import React from 'react'

export const App = (props) => {
  return <div>{props.name}</div>
}
```
### Class or Stateful Components

Class or stateful components hava state or lifecycle methods and it can change the state of the component with the help of `this.setState`. Class components create by extending `React.component` and it is initialized in constructor and might have child components as well. Here is an example.

```jsx
import React from 'react
import ToDoList from './ToDoList'

export default class Dashbord extends React.component{
  constructor(props){
   super(props)
   this.state = {}
  }
  render() {
   return(
    <div >
     <ToDoList />
    </div>
   )
  }
    
  }
}
```

### Controlled Component

Controlled component is technique which handles input form, Form elements typically maintain there own state, React maintain state in the state property of the component. we can combine both to control input forms, This is call it a controlled component. So, In controlled component form data is handled by React component.

Here is an example. when user enter the name on todo item and we can invoking javascript function `onChange()` to caputure the value of every keystroke and put it into the state so that we can use the data from the state in `onSubmit()`.

```jsx
import React from 'react';
import Form from 'react-bootstrap/Form';
import Button from 'react-bootstrap/Button';
import Row from 'react-bootstrap/Row';
import Col from 'react-bootstrap/Col';

export class ToDoForm extends React.Component {
    constructor(props) {
      super(props);
      this.state = {value: ''};
  
      this.handleChange = this.handleChange.bind(this);
      this.handleSubmit = this.handleSubmit.bind(this);
    }
  
    handleChange(event) {
      this.setState({value: event.target.value});
    }
  
    handleSubmit(event) {
      alert('A name was submitted: ' + this.state.value);
      event.preventDefault();
    }
  
    render() {
      return (
          <div className="todoform">
            <Form>
                <Form.Group as={Row} controlId="formHorizontalEmail">
                    <Form.Label column sm={2}>
                    <span className="item">Item</span>
                    </Form.Label>
                    <Col sm={5}>
                        <Form.Control type="text" placeholder="Todo Item" />
                    </Col>
                    <Col sm={5}>
                        <Button variant="primary" type="submit">Add</Button>
                    </Col>
                </Form.Group>
            </Form>
         </div>
      );
    }
  }
```

### Uncontrolled Component

Most of times it is recommended to use a controlled component, but there is an alternative approach called uncontrolled component to handle form data for this by using `Ref`. In controlled component, `Ref` used to access form value directly from the DOM instead of event hendles.

Here is an example. We create the same form with `Ref` instead of using React state. Wo define `Ref` with `React.createRef` and pass that input form and accessing form value directly from the DOM in `hanldeSubmit` method.

```jsx
import React from 'react';
import Form from 'react-bootstrap/Form';
import Button from 'react-bootstrap/Button';
import Row from 'react-bootstrap/Row';
import Col from 'react-bootstrap/Col';

export class ToDoForm extends React.Component {
    constructor(props) {
      super(props);
      this.state = {value: ''};
      this.input = React.createRef();
  
      this.handleSubmit = this.handleSubmit.bind(this);
    }
  
    handleSubmit(event) {
      alert('A name was submitted: ' + this.input.current.value);
      event.preventDefault();
    }
  
    render() {
      return (
          <div className="todoform">
            <Form>
                <Form.Group as={Row} controlId="formHorizontalEmail">
                    <Form.Label column sm={2}>
                    <span className="item">Item</span>
                    </Form.Label>
                    <Col sm={5}>
                        <Form.Control type="text" placeholder="Todo Item" ref={this.input}/>
                    </Col>
                    <Col sm={5}>
                        <Button variant="primary" onClick={this.handleSubmit} type="submit">Add</Button>
                    </Col>
                </Form.Group>
            </Form>
         </div>
      );
    }
  }
```

### Container Components

Container components are the components which deal with feching data, subscribing to redux `store`. They contain presentational components and other container components. But they don't have any HTML in it.

### Higher Order Components

Higher Order Components are the components which take a component as a argument and produce another component. Redux `connect` is the example of a higher order component. This is a powerful technique for producing reusable components.
