# 把nodejs的StoCData对象抽象后的StoCData对象

## 打开实验文件

### 调试环境：
单击右方的[ctx-response](https://codesandbox.io/s/koajs-ctx-response-pckry)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
const Koa = require("koa");
const app = new Koa();

const main = (ctx) => {
  if (ctx.request.accepts("xml")) {
    ctx.response.type = "xml";
    ctx.response.body = "<data>Hello World</data>";
  } else if (ctx.request.accepts("json")) {
    ctx.response.type = "json";
    ctx.response.body = { data: "Hello World" };
  } else if (ctx.request.accepts("html")) {
    ctx.response.type = "html";
    ctx.response.body = "<p>Hello World</p>";
  } else {
    ctx.response.type = "text";
    ctx.response.body = "Hello World";
  }
};

app.use(main);
app.listen(3000);
```

## Reference

1. [**Response**](https://koajs.com/#response)
2. [**response type**](https://github.com/ruanyf/koa-demos#demo03-response-type)



