---
layout: post
title: "Why to use Strict Mode in JavaScript ?"
author: "Ayan Bag"
categories: blog
tags: [javascript]
image: 
---

JavaScript **strict mode** is a new feature in ECMAScript 5 that enables us to code a program, or a method in a "strict" operating context. It means, the errors which are being ignored by the compiler, will throw an exception message. It is a way to opt into a restricted version of JavaScript i.e implicitly opting-out of "sloppy mode".

For example, in non-strict mode if you initialize a variable without declaring it using the ```var``` keyword (e.g. ```x = 6;```),  JavaScript interpreter will assume that you were referring to a global variable and if no such variable existed, it will automatically create one.



---
## Why Enable JavaScript Strict Mode ?

- It makes easier to write "Secure" JavaScript Code.

- It restrict the features that are unclear or poorly thought out.

- It eliminates some **JavaScript Silent Errors** by changing them to throw errors.

- It fixes mistake that make it difficult for JavaScript engines to perform optimization.

- It prohibits the use of potential reserved words which are likely to be defined in the future version of ECMAScript.

  

---
## Invoking JavaScript Strict Mode

Strict Mode can be invoked / enabled by two different ways  by using `use strict`:
- can be defined in the global scope for the entire script
- can be defined in individual function

```javascript
'use strict'; //....To invoke Strict Mode

//.....Some JS Code

```

OR

```javascript
(function() {
  'use strict'; //....To invoke Strict Mode

  // ...your code...
})()
```

**NOTE** : Ensure that `'use strict';` is at the top of the whole script or at the beginning of the function. Otherwise Strict mode may not be enabled. Only Comments appear before `'use strict';` .



---
## JavaScript Strict Mode Support

Every modern browser such as chrome, Firefox, opera, etc. and node supports and has supported strict mode for years. It is very safe feature to use. If the browser does not support strict mode the expression is simply ignored. It is just a string followed by a semi-colon, a perfectly legal JavaScript statement.



---
## General Restriction of Strict Mode

Strict Mode changes both syntax and runtime behavior. The following general restriction will be enforced if we enable Strict mode :

### Undeclared Variable are Not Allowed

In strict mode, all variable should be declared. If you assign a undeclared variable it will throw a ReferenceError.

```
"use strict";

function strict() {
    msg = "Hello World!"; // ReferenceError: msg is not defined
    return msg;
}
console.log(strict());
```



### Deleting a function or variable is not allowed

In Strict Mode, if you try to delete a variable or a function, a syntax error will be thrown.

```javascript
"use strict";

var per = {name: "John", age: 78};
delete per; // SyntaxError
```
Similarly, when you try to delete a function in strict mode you will get an syntax error:

```javascript
"use strict";

function sub(a, b) {
    return a - b;
}
delete sum; // SyntaxError

```



### Duplicating a parameter is not allowed 

In strict mode, if a function declaration has two or more parameters with same name, a syntax error will be thrown.

```javascript
"use strict";

function square(a, a) { // SyntaxError
    return a * a;
}
console.log(square(2, 2));

```



### The eval and arguments cannot be used as Identifiers

In strict mode, `eval` and `arguments` are treated like keywords , so it cannot be used as a variable names, function names and or as parameter names.

```javascript
"use strict";

var eval = 10; // SyntaxError
console.log(eval);
```



### "with" statement is not allowed

In strict mode, the `with` statement is not allowed. The `with` statement adds the properties and methods of the object to the current scope. So, the statements nested inside the `with` statement can call the properties and methods of the object directly without referring it.

```javascript
"use strict";

var radius = 2;
with(Math) { // SyntaxError
    var area = PI * radius * radius;
} 
```



### Octal Literals and Escaped Characters Not Allowed

In strict mode, octal numbers (numbers prefixed with a zero e.g. 010, 0377) are not allowed, though it is supported by all modern browser in non-strict mode. 

Strict mode forces you to be more explicit with this declaration by requiring a leading 0o in front of the octal value.

```javascript
"use strict";

var r = 010;     // SyntaxError
var s = "\010"   // SyntaxError
console.log(parseInt(r));
```



### The eval Method Cannot Alter Scope

For security reason, code passed to `eval()` cannot declare/modify variables or define function in surrounding scope.

```javascript
"use strict";

eval("var x = 5;");
console.log(x); // ReferenceError: x is not defined
```



### Can't Write to Read-Only Properties

```javascript
"use strict"; 
var objX = {}, 
objY = {get x() {return 0} };

Object.defineProperty(objX, "x", {
  value:0, writable:false
});

objX.x = 3.14; // This will cause an error

objY.x = 3.14; // This will cause an error
```



### Future Keywords cannot be used in Strict Mode

As per the latest ECMAScript 6 (or ES6) standards, these keywords are reserved keywords when they are found in strict mode code: 
- `await`
- `implements`
- `interface`
- `package`
- `private`
- `protected`
- `public`
- `static`
- `let`
- `yield`

```javascript
"use strict";
var let = 1500;      // This will cause an error 

```



---
## Wrapping Script Mode 

Strict mode is a way to ensure your code is clean and free from common syntax errors. By using Strict Mode in JavaScript, you will able to find and fix common coding mistakes and 
typos.



---
## References:

- [ECMAScript 5](https://es5.github.io/)
- [Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)




