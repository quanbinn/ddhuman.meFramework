# 使用try..catch语句处理程序运行错误

## 打开实验文件

### 调试环境1：
单击右方的[在线代码段Url网址](http://www.pythontutor.com/visualize.html#mode=edit)，浏览器里会打开一个新的页面，把下面的这些html/js/css代码段分别拷贝到空白栏中。

### 调试环境2：
- 单机右方的[Online Plunker](https://plnkr.co/edit/?open=lib%2Fscript.js)，稍后在浏览器里会显示js的运行环境。
- 把下面的这些html/js/css代码段分别拷贝到的相应的文件空白栏中， 然后单击右上方的按键“Preview”。

```html
<!DOCTYPE html>
<script>
'use strict';

// let error = new Error(message);
// let error = new SyntaxError(message);
// let error = new ReferenceError(message);

let error = new Error("Things happen o_O");

alert(error.name); // Error
alert(error.message); // Things happen o_O
</script>
```

```html
<!DOCTYPE html>
<script>
'use strict';

let json = '{ "age": 30 }'; // incomplete data

try {

  let user = JSON.parse(json); // <-- no errors

  if (!user.name) {
    throw new SyntaxError("Incomplete data: no name"); // (*)
  }

  alert( user.name );

} catch(e) {
  alert( "JSON Error: " + e.message ); // JSON Error: Incomplete data: no name
}
</script>
```

## Reference

1. [Exception handling](https://en.wikipedia.org/wiki/Exception_handling)
2. [**try...catch from MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch)
3. [**Error handling, "try..catch"**](https://javascript.info/try-catch)



