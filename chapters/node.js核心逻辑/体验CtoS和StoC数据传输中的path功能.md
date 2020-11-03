# 体验CtoS和StoC数据传输中的path功能

## 打开实验文件

### 调试环境：
单击右方的[体验CtoS和StoC数据传输中的path功能 from repl.it](https://repl.it/@quanbinn/Ti-Yan-CtoSHe-StoCShu-Ju-Chuan-Shu-Zhong-De-pathGong-Neng)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### index.js

```javascript
var path = require("path");

path.resolve('/foo/bar', './baz');
// 返回: '/foo/bar/baz'

path.resolve('/foo/bar', '/tmp/file/');
// 返回: '/tmp/file'

path.resolve('wwwroot', 'static_files/png/', '../gif/image.gif');
// 如果当前工作目录为 /home/myself/node，
// 则返回 '/home/myself/node/wwwroot/static_files/gif/image.gif'

path.relative('/data/orandea/test/aaa', '/data/orandea/impl/bbb');
// 返回: '../../impl/bbb'

// 格式化路径
console.log('normalization : ' + path.normalize('/test/test1//2slashes/1slash/tab/..'));

// 连接路径
console.log('joint path : ' + path.join('/test', 'test1', '2slashes/1slash', 'tab', '..'));

// 转换为绝对路径
console.log('resolve : ' + path.resolve('main.js'));

// 路径中文件的后缀名
console.log('ext name : ' + path.extname('main.js'));
```

## Reference

1. [Node.js Path 模块 **from runoob.com**](https://www.runoob.com/nodejs/nodejs-path-module.html)



