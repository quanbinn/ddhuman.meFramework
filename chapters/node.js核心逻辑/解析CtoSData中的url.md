# 解析CtoSData中的url

## 打开实验文件

### 调试环境：
单击右方的[解析CtoSData中的url from tutorialspoint.com](http://tpcg.io/FwK61OlD)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

```javascript
let url = require('url');
let address = 'http://www.ddhuman.me/default.htm?year=2017&month=february';
//Parse the address:
let request = url.parse(address, true);

/*The parse method returns an object containing url properties*/
console.log(request.host);
console.log(request.pathname);
console.log(request.search);

console.log(request.protocol); 
console.log(request.hostname);
console.log(request.port);  
console.log(request.hash);

/*The requestuery property returns an object with all the requestuerystring parameters as properties:*/
let reqData = request.query;
console.log(reqData.month);
```

## Reference

1. [Node.js URL Module **from w3schools.com**](https://www.w3schools.com/nodejs/nodejs_url.asp)



