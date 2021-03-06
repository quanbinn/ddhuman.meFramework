# 连接MongoDB后CRUD-Database

## 在Ubuntu上安装MongoDB并操作它的核心逻辑

1. 在web上下载相应的MongoDB版本到Ubuntu版本的服务器 (文件集合)

2. 在服务器上运行MongoDB（文件集合），生成了用javascript函数调用的API

3. 调用javascrip函数的API, CRUD-Database 

   （**node.js写了一系列函数调用MongoDB提供的javascript API**）

### user.js

```javascript
// model/user.js
'use strict';

module.exports = app => {
  const mongoose = app.mongoose;
  const Schema = mongoose.Schema;

  const UserSchema = new Schema({
    username: { type: String },
    password: { type: String },
  });

  return mongoose.model('User', UserSchema);
}

// controller/user.js
'use strict';

const Controller = require('egg').Controller;

class UserController extends Controller {
  async index() {
    const { ctx } = this;
    // let yuhangxia  = {username: "yuhangxia", password: "dsafsdaf"};
    // await ctx.model.User.create(yuhangxia);
    const users = await ctx.model.User.find({});
    ctx.body = users.join("|");
  }
}

module.exports = UserController;
```

## Reference

1. [**MongoDB JavaScript tutorial**](http://zetcode.com/javascript/mongodb/)
2. [How To Install MongoDB on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-18-04-source#:~:text=%20How%20To%20Install%20MongoDB%20on%20Ubuntu%2018.04,As%20mentioned%20previously%2C%20the%20installation%20process...%20More%20)



