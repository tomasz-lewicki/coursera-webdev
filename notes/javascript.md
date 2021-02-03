- All arguments to a javascript function are optional!

# Scopes
There are two scopes:
- global scope 
- function scope

# Scope chain
    - we first look for a variable in the current scope 
    - then recursively in its parent scopes
    - parent scope is the scope where the function is __defined__, not __executed__!
    - if not found in the `global` scope, the variable is `undefined`


# Types in javascript
- Object Type
- Primitive Types: single, immutable value
    - true, false
    - `undefined`
    - `null`
    - Number type: always represented as `float64`. Integers are just a subset of `Number`
    - Symbol

```js
var x;
console.log(x); // ReferenceError: x is not defined
x == undefined; // evaluates to true
```

the value of `undefined` means that memory has been allocated, but the value was never explicitly set.


# Constructs

* String concatination
```js
var s1 = "hello";
s1 += " world!";
```

* Type auto conversions
```js
4 == '4' // will evaluate to true
4 === '4' // strict conversion: will
```

* curly braces should start on the same line
```js
function f()
{
    return
    {
        name: 'Tomek';
    }
}

f(); // will return `undefined`
```


* Functions are Objects too!
* Why it's important to use `new` keyword?
    - we not only want to exectue the constructor
    - but also register all the functions from the prototype


* __Hoisting__ is the reason the snippet below works:
```js
catName("Chloe");

function catName(name) {
  console.log("My cat's name is " + name);
}
```

# Arrays
Arrays are also objects in JS. So this is perfectly valid:
```js
arr = new Array();
arr[0] = 'd';
arr[1] = 'u';
arr[2] = 'p';
arr.hehe = 555;
```

# Closures
Preserve outer lexical environment for the function.

# Namespaces
* There are no namespaces in javascript.
* You can bind functions and variables to an object in order to achieve namespace-like behavior

# IIFE 
* Immediately invoked function expression
* We can use it to create fake namespaces
* Example:
```js
(function (name) {
    console.log("hello " + name);
})("Tomek"); // <- this line immediately executes the function
```

# DOM 

* `document` is a special object that lets us access the html elements in the web page
* `document instanceof HTMLDocument` evaluates to `true`
* Place your js at the end of the `body`.
* Why? so all ids are loaded, and you can get their objects by `document.getElementById()`


### Methods to get html elements from DOM

- `document.getElementById()`
- `document.querySelector("h1")` _(gets the first `h1` elem)_
- `document.querySelectorAll(".example-class")` _(returns a NodeList of elements)_

### Events
- `onclick`, `onblur`, etc.
- you can register events either:
    + directly in html
    ```html
    <button onclick="sayHello();"></button> // `this` points to window
    ```
    + by registering events in javascript (doesn't pollute your html):
    ```js
    document.querySelector("button").onclick = sayHello; // `this` points to button (somewhat more flexible)
    ```
    +  


# AJAX

- HTTP: a request/response stateless protocol
- _URI_: uniform resource identifier `api/v2/measurements`
- _URL_: uniform resource locator `http://air.com/api/v2/measurements`