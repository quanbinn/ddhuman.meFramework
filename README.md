# DDHuman.Me Framework

## egg.js核心逻辑

- [控制与request响应的response内容的**Router**](/chapters/egg.js核心逻辑/控制与request响应的response内容的Router.md)
- [解析用户输入/返回处理后结果的**Controller**类](/chapters/egg.js核心逻辑/解析用户输入-返回处理后结果的Controller类.md)
- [**连接MongoDB**后CRUD-Database](/chapters/egg.js核心逻辑/连接MongoDB后CRUD-Database.md)
- [渲染与request响应的response内容的**View**功能](/chapters/egg.js核心逻辑/渲染与request响应的response内容的View功能.md)
- [理解egg-init的加载原理和过程](/chapters/egg.js核心逻辑/理解egg-init的加载原理和过程.md)

|     this    | this.ctx  | this.ctx.req | this.ctx.res |
| :----------: | :------: | :----------: | :----------: |
|  [this]   | [ctx] |  [req]   |  [res]   |

[this]: /chapters/egg.js核心逻辑/this.md
[ctx]: /chapters/egg.js核心逻辑/ctx.md
[req]: /chapters/egg.js核心逻辑/req.md
[res]: /chapters/egg.js核心逻辑/res.md

## 代办事项的一步步教程

1. [Creating an app](/chapters/一步步教程_代办事项应用/Creating_an_app.md)
2. [Templates OR Components](/chapters/一步步教程_代办事项应用/Components.md)
3. [Collections](/chapters/一步步教程_代办事项应用/Collections.md)
4. [Forms and events](/chapters/一步步教程_代办事项应用/Forms_and_events.md)
5. [Update and remove](/chapters/一步步教程_代办事项应用/Update_and_remove.md)

## koa.js核心逻辑

- [包含一系列中间件函数的app对象](/chapters/koa.js核心逻辑/包含一系列中间件函数的app对象.md)
- [把nodejs的CtoSData和StoCData对象封装到一起的Context对象](/chapters/koa.js核心逻辑/把nodejs的CtoSData和StoCData对象封装到一起的Context对象.md)
- [把nodejs的CtoSData对象抽象后的CtoSData对象](/chapters/koa.js核心逻辑/把nodejs的CtoSData对象抽象后的CtoSData对象.md)
- [把nodejs的StoCData对象抽象后的StoCData对象](/chapters/koa.js核心逻辑/把nodejs的StoCData对象抽象后的StoCData对象.md)

## vue.js核心逻辑

- 典型*.vue

| experiment | equipment |
|:-------:|:-------:|
|[VUE_showAnExperiment]|[VUE_learningEquip]|
|[VUE_showExperiments]|[VUE_workingEquip]|
|                   |[VUE_exerciseEquip]|

[VUE_showAnExperiment]: /chapters/vue.js核心逻辑/showAnExperiment.md
[VUE_showExperiments]: /chapters/vue.js核心逻辑/showExperiments.md

[VUE_learningEquip]: /chapters/vue.js核心逻辑/learningEquip.md
[VUE_workingEquip]: /chapters/vue.js核心逻辑/workingEquip.md
[VUE_exerciseEquip]: /chapters/vue.js核心逻辑/exerciseEquip.md

- HTTP请求后对Database的CRUD
  - [对Database进行CRUD操作](/chapters/vue.js核心逻辑/对Database进行CRUD操作.md)
  - [GET请求后取得Database数据](/chapters/vue.js核心逻辑/GET请求后取得Database数据.md)
  - [POST请求后写入Database数据](/chapters/vue.js核心逻辑/POST请求后写入Database数据.md)
  - [PUT请求后覆写Database数据](/chapters/vue.js核心逻辑/PUT请求后覆写Database数据.md)
  - [DELETE请求后删除Database的数据](/chapters/vue.js核心逻辑/DELETE请求后删除Database中的数据.md)
  - [取Database数据-->用Template-->Render成html](/chapters/vue.js核心逻辑/从Database取得数据通过TemplateRender成html文件.md)
- 背后的数据结构和算法
  - [体验html页面的DOM结构和节点数据](/chapters/vue.js核心逻辑/体验html页面的DOM结构和节点数据.md)
  - [用js创建html页面中的标签内容](/chapters/vue.js核心逻辑/用js创建html页面中的标签内容.md)
  - [理解Virtual DOM和diff()](/chapters/vue.js核心逻辑/理解Virtual_DOM和diff().md)

## node.js核心逻辑

- [使用python体验socket](/chapters/node.js核心逻辑/使用python体验socket.md)
- Client <----> Server数据传输中的重要功能
	- [创建createServer()处理CtoSData和StoCData](/chapters/node.js核心逻辑/创建createServer()处理CtoSData和StoCData.md)
	- [解析CtoSData中的url](/chapters/node.js核心逻辑/解析CtoSData中的url.md)
	- [体验CtoS和StoC数据传输中的stream](/chapters/node.js核心逻辑/体验CtoS和StoC数据传输中的stream.md)
	- [体验CtoS和StoC数据传输中对file的**CRUD**操作](/chapters/node.js核心逻辑/体验CtoS和StoC数据传输中对file的CRUD操作.md)
	- [体验CtoS和StoC数据传输中的path功能](/chapters/node.js核心逻辑/体验CtoS和StoC数据传输中的path功能.md)

## JS(ES6)核心逻辑

- 使用python体验多线程和多进程
	- [多线程](/chapters/JS(ES6)核心逻辑/使用python体验多线程.md)
	- [多线程同步](/chapters/JS(ES6)核心逻辑/使用python体验多线程同步.md) 
	- [多进程](/chapters/JS(ES6)核心逻辑/使用python体验多进程.md)
- 体验异步的实现方式
  - [在1个函数中把另外1个函数作为参数调用的callback](/chapters/JS(ES6)核心逻辑/在1个函数中把另外1个函数作为参数调用的callback.md)
  - [使callback写起来更简洁&更合理的Promise对象](/chapters/JS(ES6)核心逻辑/使callback写起来更简洁&更合理的Promise对象.md)
  - [使Promise写起来更简洁，更合理的async+await风格](/chapters/JS(ES6)核心逻辑/使Promise写起来更简洁，更合理的async+await风格.md)
- 体验基本用法
  - [采用strict mode使代码运行安全，并且提高编译效率](/chapters/JS(ES6)核心逻辑/采用strict_mode使代码运行安全&提高编译效率.md)
  - [调用子文件中多种对象的module功能](/chapters/JS(ES6)核心逻辑/调用子文件中多种对象的module功能.md)
  - [让函数表达式看起来更简洁的=>写法](/chapters/JS(ES6)核心逻辑/让函数表达式看起来更简洁的Arrow写法.md)
  - [使用try..catch语句处理程序运行错误](/chapters/JS(ES6)核心逻辑/使用try..catch语句处理程序运行错误.md)
  - [class的典型用法](/chapters/JS(ES6)核心逻辑/class的典型用法.md)

## 附录

- 网络存储原型Data
  - [images](/chapters/附录/网络存储原型Data的images.md)
  - [videos](/chapters/附录/网络存储原型Data的videos.md)
  - [audios](/chapters/附录/网络存储原型Data的audios.md)


