# 把nodejs的CtoSData和StoCData对象封装到一起的Context对象

## 打开实验文件

### 调试环境：
单击右方的[ctx](https://codesandbox.io/s/koajs-ctx-864ff)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js
```javascript
const fs = require("fs");
const Koa = require("koa");
const app = new Koa();

const main = (ctx) => {
  ctx.response.type = "html";
  ctx.response.body = fs.createReadStream("./template.html");
};

app.use(main);
app.listen(3000);
```

```html
<!DOCTYPE html>

<html lang="en">
  <head>
    <meta charset="utf-8" />

    <title>The HTML5 Herald</title>
    <meta name="description" content="HTML5 Template" />
    <meta name="author" content="xxx" />
  </head>

  <body>
    <h1>Hello ddhuman.me</h1>
  </body>
</html>
```

## Reference

1. [**Context**](https://koajs.com/#context)
2. [**use a template**](https://github.com/ruanyf/koa-demos#demo04-use-a-template)



