# 体验CtoS和StoC数据传输中的stream

## 打开实验文件

### 调试环境：
单击右方的[体验CtoS和StoC数据传输中的stream from repl.it](https://repl.it/@quanbinn/Ti-Yan-CtoSHe-StoCShu-Ju-Chuan-Shu-Zhong-Dui-fileDe-CRUDCao-Zuo)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
var fs = require("fs");  
var data = '';  
// Create a readable stream  
var readerStream = fs.createReadStream('input.txt');  
// Set the encoding to be utf8.   
readerStream.setEncoding('UTF8');  
// Handle stream events --> data, end, and error  
readerStream.on('data', function(chunk) {  
   data += chunk;  
});  
readerStream.on('end',function(){  
   console.log(data);  
});  
readerStream.on('error', function(err){  
   console.log(err.stack);  
});  
console.log("Program Ended");  
```

### input.txt
```txt
binxia is testing the file.
```

### index.js(another example)
```javascript
var fs = require("fs");
var data = '菜鸟教程官网地址：www.runoob.com';

// 创建一个可以写入的流，写入到文件 output.txt 中
var writerStream = fs.createWriteStream('output.txt');

// 使用 utf8 编码写入数据
writerStream.write(data,'UTF8');

// 标记文件末尾
writerStream.end();

// 处理流事件 --> finish、error
writerStream.on('finish', function() {
    console.log("写入完成。");
});

writerStream.on('error', function(err){
   console.log(err.stack);
});

console.log("程序执行完毕");
```

## Reference

1. [Node.js Streams **from javatpoint.com**](https://www.javatpoint.com/nodejs-streams)
2. [Node.js Stream(流) **from runoob.com**](https://www.runoob.com/nodejs/nodejs-stream.html)



