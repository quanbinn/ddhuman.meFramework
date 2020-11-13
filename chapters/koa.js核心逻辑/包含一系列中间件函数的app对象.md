# 包含一系列中间件函数的app对象

## Koa.js的4个对象关系的重要逻辑 
1. 生成了1个包含一系列函数的app对象 -> 
2. app对象的构造函数里返回了1个ctx对象 -> 
3. ctx对象的request属性生成了1个对象ctx.request
4. ctx对象的response属性生成了1个对象ctx.response

## 打开实验文件

### 调试项目1：
单击右方的[koajs-first-example](https://codesandbox.io/s/koajs-first-example-gigk7)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
const Koa = require("koa");
const Router = require("koa-router");
const logger = require("koa-logger");
const bodyParser = require("koa-bodyparser");

const PORT = process.env.PORT || 8000;

const app = new Koa();
console.log(app);
const router = new Router();

router.get("/", async (ctx) => {
  const name = "binxia";
  ctx.body = {
    message: `Hello, ddhuman's creator: ${name}! `
  };
});

app
  .use(logger())
  .use(bodyParser())
  .use(router.routes())
  .use(router.allowedMethods())
  .listen(PORT, "0.0.0.0", () =>
    console.log(`listening on http://localhost:${PORT}...`)
  );
```

### 调试项目2：

单击右方的[understand middleware](https://codesandbox.io/s/understand-middleware-9iqfo)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
// var http = require("http");

// //create a server object:
// http
//   .createServer(function(req, res) {
//     res.write("Hello World!"); //write a response to the client
//     res.end(); //end the response
//   })
//   .listen(8080); //the server object listens on port 8080

const Koa = require("koa");
const app = new Koa();

const log = console.log;
// logger
app.use(async (ctx, next) => {
  await next();
  // middleware 1, 后执行
  const rt = ctx.response.get("X-Response-Time");
  log(`\nmiddleware 1, 后执行`, rt);
  log(`${ctx.method} ${ctx.url} - ${rt}`);
});

// x-response-time
app.use(async (ctx, next) => {
  const start = Date.now();
  await next();
  // middleware 2, 先执行
  const ms = Date.now() - start;
  log(`\nmiddleware 2, 先执行`, `${ms}ms`);
  ctx.set("X-Response-Time", `${ms}ms`);
});

// response
app.use(async (ctx, next) => {
  // log(`response ctx`, ctx);
  // await next();
  log(`\nmiddleware 0, 最后的 middleware 最先执行`);
  ctx.body = "Hello World! <br />powered by koa.js";
});

app.listen(3000);
// app.listen(8080);
```

## Reference

1. [**Application**](https://koajs.com/#application)
2. [Koa.js - Hello World](https://www.tutorialspoint.com/koajs/koajs_hello_world.htm)
3. [Koa 洋葱模型](https://www.cnblogs.com/xgqfrms/p/12842176.html)
4. [**koa-demos** from 阮一峰](https://github.com/ruanyf/koa-demos)



