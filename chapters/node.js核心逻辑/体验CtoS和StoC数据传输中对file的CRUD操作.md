# 体验CtoS和StoC数据传输中对file的CRUD操作

## Read

单击右方的[体验CtoS和StoC数据传输中对file的R操作 from repl.it](https://repl.it/@quanbinn/Ti-Yan-CtoSHe-StoCShu-Ju-Chuan-Shu-Zhong-Dui-fileDe-RCao-Zuo)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
var fs = require("fs");

// 异步读取
fs.readFile('input.txt', function (err, data) {
   if (err) {
       return console.error(err);
   }
   console.log("异步读取: " + data.toString());
});

// 同步读取
var data = fs.readFileSync('input.txt');
console.log("同步读取: " + data.toString());

console.log("程序执行完毕。"); 
```

### input.txt
```txt
菜鸟教程官网地址：www.runoob.com
文件读取实例
```

## Create+Update

### 调试环境：
单击右方的[体验CtoS和StoC数据传输中对file的U操作 from repl.it](https://repl.it/@quanbinn/Ti-Yan-CtoSHe-StoCShu-Ju-Chuan-Shu-Zhong-Dui-fileDe-UCao-Zuo)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
var fs = require("fs");

console.log("准备写入文件");
fs.writeFile('input.txt', '我是通 过fs.writeFile 写入文件的内容',  function(err) {
   if (err) {
       return console.error(err);
   }
   console.log("数据写入成功！");
   console.log("--------我是分割线-------------")
   console.log("读取写入的数据！");
   fs.readFile('input.txt', function (err, data) {
      if (err) {
         return console.error(err);
      }
      console.log("异步读取文件数据: " + data.toString());
   });
});
```

### input.txt
```txt
test update
```

## Delete

### 调试环境：
单击右方的[体验CtoS和StoC数据传输中对file的D操作 from repl.it](https://repl.it/@quanbinn/Ti-Yan-CtoSHe-StoCShu-Ju-Chuan-Shu-Zhong-Dui-fileDe-DCao-Zuo)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
var fs = require("fs");

console.log("准备删除文件！");
fs.unlink('input.txt', function(err) {
   if (err) {
       return console.error(err);
   }
   console.log("文件删除成功！");
});
```

### input.txt
```txt
test delete!
```

## Reference

1. [Node.js 文件系统 **from runoob.com**](https://www.runoob.com/nodejs/nodejs-fs.html)




