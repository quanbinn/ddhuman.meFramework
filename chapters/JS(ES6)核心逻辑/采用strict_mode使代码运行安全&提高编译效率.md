# 采用strict mode使JS代码运行安全，并且提高编译效率

- Strict mode changes previously accepted "bad syntax" into real errors. As an example, in normal JavaScript, **mistyping a variable name creates a new global variable.** **In strict mode, this will throw an error, making it impossible to accidentally create a global variable**. 

- In normal JavaScript, **a developer will not receive any error feedback assigning values to non-writable properties**. In strict mode, **any assignment to a non-writable property, a getter-only property, a non-existing property, a non-existing variable, or a non-existing object, will throw an error**.

单击右方的[在线代码段Url网址](http://pythontutor.com/visualize.html#code='use%20strict'%3B%0A%0Aheight%20%3D%201.74%3B%20//%20throws%20a%20ReferenceError%3A%20height%20is%20not%20defined%0Aweight%20%3D%2063.5%3B%20//%20throws%20a%20ReferenceError%3A%20weight%20is%20not%20defined%0A%0Alet%20height%20%3D%201.74%3B%20%0A//%20let%20height%20%3D%20010%3B%20//%20throws%20a%20SyntaxError%3A%20Octal%20literals%20are%20not%20allowed%0A//%20let%20height%20%3D%20%22%5C010%22%3B%20//%20throws%20a%20SyntaxError%3A%20Octal%20literals%20are%20not%20allowed&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
'use strict';

height = 1.74; // throws a ReferenceError: height is not defined
weight = 63.5; // throws a ReferenceError: weight is not defined

let height = 1.74; 
// let height = 010; // throws a SyntaxError: Octal literals are not allowed
// let height = "\010"; // throws a SyntaxError: Octal literals are not allowed
```

## Reference

1. [Quirks mode = Strict mode from **Wikiperia**](https://en.wikipedia.org/wiki/Quirks_mode)
2. [Strict mode from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)
3. [**JavaScript Use Strict from w3schools.com**](https://www.w3schools.com/js/js_strict.asp)
4. [**The modern mode, "use strict"**](https://javascript.info/strict-mode)




