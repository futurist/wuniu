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

*it's have some features in Java™, Self(prototype-oriented), and Scheme(first-class functions)*

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

    sqrt then sqrt of number in Scheme

    ```scheme
    (define (f x y) (x (x y)))
    (display (f sqrt 16))
    ```
********

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
   - Object.prototype create
     1. inheritance
     2. shared properties
   - should with `new`, w/o will lead to *special effect*
     `Date()` result is *string*
     `new Date()` result is *object*
   - prototype chain (instance.__proto__)
