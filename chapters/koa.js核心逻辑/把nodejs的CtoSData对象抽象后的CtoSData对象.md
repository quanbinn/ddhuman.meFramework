# 把nodejs的CtoSData对象抽象后的CtoSData对象

## 打开实验文件

### 调试环境：
单击右方的[ ctx-request](https://codesandbox.io/s/koajs-ctx-request-frypw)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
const Koa = require("koa");
const app = new Koa();

const main = (ctx) => {
  if (ctx.request.path !== "/") {
    ctx.response.type = "html";
    ctx.response.body = '<a href="/">Index Page</a>';
  } else {
    ctx.response.body = "DDHuman.me's experiment 1";
  }
};

app.use(main);
app.listen(3000);
```

## Reference

1. [**Request**](https://koajs.com/#request)
2. [**Simple router**](https://github.com/ruanyf/koa-demos#demo05-simple-router)



