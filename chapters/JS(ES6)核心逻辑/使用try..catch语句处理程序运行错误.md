# 使用try..catch语句处理程序运行错误

## 打开实验文件

- 单机右方的[Online Plunker](https://plnkr.co/edit/?open=lib%2Fscript.js)，稍后在浏览器里会显示js的运行环境。
- 把下面的这些html/js/css代码段分别拷贝到的相应的文件空白栏中， 然后单击右上方的按键“Preview”。

```html
<!DOCTYPE html>
<script>
'use strict';

/*
let error = new Error("测试一个Error");
console.log(error.name); // Error
console.log(error.message); // 测试一个Error

let error = new ReferenceError("测试一个ReferenceError");
console.log(error.name); // ReferenceError
console.log(error.message); // 测试一个ReferenceError
*/

let error = new SyntaxError("测试一个SyntaxError");
console.log(error.name); // SyntaxError
console.log(error.message); // 测试一个SyntaxError

</script>
```

```html
<!DOCTYPE html>
<script>
'use strict';

let json = '{ "age": 30 }'; // incomplete data
// let json = '{  "name": "Binxia", "age": 30 }'; // complete data
  
try {

  let user = JSON.parse(json); // <-- no errors

  if (!user.name) {
    throw new SyntaxError("Incomplete data: no name"); // (*)
  }

  console.log( user.name );

} catch(e) {
  alert( "JSON Error: " + e.message ); // JSON Error: Incomplete data: no name
}
</script>
```

## Reference

1. [Exception handling](https://en.wikipedia.org/wiki/Exception_handling)
2. [**try...catch from MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch)
3. [**Error handling, "try..catch"**](https://javascript.info/try-catch)



