# 创建createServer()处理CtoSData和StoCData

## 打开实验文件

### 调试环境：
单击右方的[创建createServer()处理CtoSData和StoCData](https://repl.it/@quanbinn/Chuang-Jian-createServerChu-Li-CtoSDataHe-StoCData)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
var http = require('http');

http.createServer(function (request, response) {

    // 发送 HTTP 头部 
    // HTTP 状态值: 200 : OK
    // 内容类型: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});

    // 发送响应数据 "Hello World"
    response.end('Hello World\n');
}).listen(8888);

// 终端打印如下信息
console.log('Server running at http://127.0.0.1:8888/');
```

## Reference

1. [Node.js 创建第一个应用 **from runoob.com**](https://www.runoob.com/nodejs/nodejs-http-server.html)



