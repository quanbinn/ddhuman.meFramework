# 解析用户输入/返回处理后结果的Controller类

### app/controller/home.js
```javascript
'use strict';

const Controller = require('egg').Controller;

class HomeController extends Controller {
  async index() {
    const { ctx } = this;
    ctx.body = 'hi, egg';
  }
}

module.exports = HomeController;
```

## Reference

1. [控制器（Controller）](https://eggjs.org/zh-cn/basics/controller.html)



