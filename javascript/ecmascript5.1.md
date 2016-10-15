# ECMAScript 5.1

## Definition

ECMAScript is an object-oriented scripting language for performing computations and manipulating computational objects within a host environment.

- **Host environment** Provide objects and facilities exposing functionality to scripting control, see [World of ECMAScript][].
  1. Client side:
     - Web Browser (IE, Safari, Chrome, Firefox)
     - PDF (MuPDF, Adobe Reader)
     - Flash (ActionScript)
     - Photoshop
  2. Non-client side:
     - Server (Node.JS, MongoDB, CouchDB)
     - Hardware (Espruino, Cesanta, Internet of Things)

[World of ECMAScript]: http://ejohn.org/blog/the-world-of-ecmascript/

- **Scripting language** A programming language that is used to manipulate, customise, and automate the facilities of an existing system,
intended for use by both professional and non-professional programmers.

### Short History

In May 1995, Netscape hired Brendan Eich to make a lightweight programming language to add interactivity to HTML pages. The first version of the language build in 10 days, mixed some features in Java, Self, and Scheme.

Java: language structure, the primitive value and Object as data types
Self: prototype-oriented
Scheme: first-class functions, closure

********
**Reference**
[The Past, Present, and Future of JavaScript][]
[The Past, Present, and Future of JavaScript]: http://cdn.oreillystatic.com/oreilly/radarreport/0636920026969/past-present-and-future-of-javascript.pdf

********
**TASK**

1. Open browser and make script to control input.
   - open `baidu.com`
   - type console `kw.value = 123`
   - explain what happened!

2. Introduce *Self* [optional]
   - explain what is prototype? (like TV, the signal is Prototype, the screen is Instance)
   - `labelWidget copy label: 'Hello, World!'.`
   - Javascript code demo

   ```Javascript
   var img = new Image()
   img.src = 'logo.png'
   document.body.appendChild(img)
   ```

3. Introduce *Scheme* [optional]

   - sqrt then sqrt of number in Scheme

    ```scheme
    (define (f x y) (x (x y)))
    (display (f sqrt 16))
    ```
   - Javascript code demo

    ```Javascript
    var img = new Image()
    img.src = 'logo.png'
    document.body.appendChild(img)
    ```

## Language Overview

ECMAScript program is a cluster of communicating objects:
- Language objects
  - primitive values (5):
    with type: Undefined, Null, Boolean, Number, String

  - build-in Objects (12):
    global, Object, Function, Array, String, Boolean, Number, Math, Date, RegExp, JSON, Error

  - functions:
    callable object

- Host objects
  - Web Browser (DOM Nodes, Cookies, XHR)
  - Node.JS (fs, http)

### Object:

#### Create

1. literal notation

2. via constructors
   - Object is a constructor function
   - Object.prototype provide
     1. inheritance
     2. shared properties
   - should with `new`, w/o will lead to *special effect*
     `Date()` result is *string*
     `new Date()` result is *object*
   - instance have prototype chain (instance.__proto__)

******
**TASK**
1. Understand below code

**TEST 1**
```javascript
Function.a = 1
Function.prototype.a = 2
Function.constructor.a = 3
Function.constructor.prototype.a = 4

console.log(
  Function.a,
  Function.prototype.a,
  Function.constructor.a,
  Function.constructor.prototype.a,
  Object.a,
  Object.prototype.a,
  Object.constructor.a,
  Array.a,
  Array.constructor.a,
  Array.prototype.a
)

```

**TEST 2**
```javascript
Function.a = 1
Function.prototype.a = 2
Function.constructor.a = 3
Function.constructor.prototype.a = 4

Object.a = 5
Object.constructor.a = 6
Object.prototype.a = 7

console.log(
  Function.a,
  Function.prototype.a,
  Function.constructor.a,
  Function.constructor.prototype.a,
  Object.a,
  Object.prototype.a,
  Object.constructor.a,
  Array.a,
  Array.constructor.a,
  Array.prototype.a
)
```


**TEST 3**
```javascript

// see what is constructor
console.log(Function.constructor===Function)  //true, it's only case in JS that constructor===self

console.log(Array.constructor===Function)  //true, any constructor MUST BE a function

console.log(Object.constructor===Object)  //false


// see what is prototype
console.log(Object.prototype===Function.prototype)  //false

console.log(typeof Object.prototype, typeof Function.prototype)   //"object", "function", that's why above failed

console.log(Object.constructor.prototype===Function.prototype)  //true, see above

// Object inherit
console.log(Function.prototype.isPrototypeOf(Array))  //true

console.log(Object.prototype.isPrototypeOf(Array))  //true, Array <- Object <- Function

// prototype record it's constructor
console.log(Object.prototype.constructor===Object)  //true, also applies to Array, Date....

// object instance
var a={}
console.log(a.constructor===Object)  //true
console.log(a.constructor===Object.constructor)  //false
console.log('prototype' in a)  //false
console.log('constructor' in a)  //true
console.log('__proto__' in a)  //true
console.log(a.__proto__===Object.prototype)  //true

```

**TEST 4**
```Javascript
// try to change constructor
var proto = Object.create(null)
proto.abc = 123
proto.constructor = function(){console.log(666); return 666;}

Object.prototype = proto
Object.constructor.prototype = {}

```


### Function


### Automate Comma Insertion



### RegExp

```javascript
var slug = function(value) {
    return value.toLowerCase().replace(/\W/g, "-")
}

slug("Hello world")  // "hello-world"
```
