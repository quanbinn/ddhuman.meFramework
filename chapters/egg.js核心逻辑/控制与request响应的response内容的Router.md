# 控制与request响应的response内容的Router

## 打开实验文件

单击右方的[--- **from codesandbox.io**]()，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
```
-------------------
## Koa.js-Router

## 打开实验文件

单击右方的[koa.js: Router](https://codesandbox.io/s/koajs-router-ude1h)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
const Koa = require('koa');
const route = require('koa-route');
const app = new Koa();

const about = ctx => {
  ctx.response.type = 'html';
  ctx.response.body = '<a href="/">Index Page</a>';
};

const main = ctx => {
  ctx.response.body = 'Hello World';
};

app.use(route.get('/', main));
app.use(route.get('/about', about));

app.listen(3000);
```

## Reference

1. [路由（Router）](https://eggjs.org/zh-cn/basics/router.html)
2. [**koa-route**](https://github.com/ruanyf/koa-demos#demo06-koa-route)


