# 渲染与request响应的response内容的View功能

## 使用前端模版在Client端渲染response内容的核心逻辑

1. 后端**读取html, js, css文件中的内容**，作为**response的body**发送给**请求ip**
2. 对于**在response中使用的前端模版**，在client端从web上下载并运行相应的文件内容。例如：对于vue.js，在client端模版运行前从<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>上下载并运行相应的文件内容。
3. **运行模版文件的API**后，**response的body**渲染出预想的结果。

## 打开实验文件

单击右方的[--- **from codesandbox.io**]()，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### app/view/*.js
```javascript

```

## Reference

1. []()
2. []()



