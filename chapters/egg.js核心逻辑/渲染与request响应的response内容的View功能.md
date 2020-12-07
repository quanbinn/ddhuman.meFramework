# 渲染与request响应的response内容的View功能

## 使用前端模版在Client端渲染response内容的核心逻辑

1. 后端**读取html, js, css文件中的内容**，作为**response的body**发送给**请求ip**
2. 对于**在response中使用的前端模版**，在client端从web上下载并运行相应的文件内容。例如：对于vue.js，在client端模版运行前从<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>上下载并运行相应的文件内容。
3. **运行模版文件的API**后，**response的body**渲染出预想的结果。

## 打开实验文件

单击右方的[--- **from codesandbox.io**]()，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

### app/view/experiments/experiments.tpl
```html
<html>
  <head>
    <title>DDHuman.me</title>
  </head>
  <body>
    <div>
      {% for item in list %}
        <h1>实验名称：{{ item.title }}</h1>
        <a href="{{ item.url }}"><img src="{{ item.showImage }}" alt="{{ item.title }}" width="400"></a>
        <h1><a href="{{ item.url }}">打开链接做实验</a></h1>
        <p>类别：{{ item.tag }}</p>
      {% endfor %}
    </div>
  </body>
</html>
```

### app/controller/experiments.js

```javascript
const Controller = require('egg').Controller;

class ExperimentsController extends Controller {
  async list() {
    const _data = {
      list: [
        {
					  _id: '860f191e810c87654de974bc',
					  title: '用橡皮筋和小塑料棍感受函数某点的切线',
  					  showImage: 'https://i.ibb.co/3T89n6X/image.png',
					  url: 'https://gitee.com/quanbinn/Learn-Mathematical-Olympiad-The-Interactive-Way/blob/master/chapters/%E5%BE%AE%E5%88%86/%E7%94%A8%E6%A9%A1%E7%9A%AE%E7%AD%8B%E5%92%8C%E5%B0%8F%E5%A1%91%E6%96%99%E6%A3%8D%E6%84%9F%E5%8F%97%E5%87%BD%E6%95%B0%E6%9F%90%E7%82%B9%E7%9A%84%E5%88%87%E7%BA%BF.md',
					  tag: ['数学'],
					  createdAt: 'Wed Sep 30 2020 17:53:29 GMT+0800 (中国标准时间)', // new Date()
					  creator: 'QwkSmREWsw5KDx3L7'  // userId()	
                  },
                  {
					  _id: '860f191e810c19729de974ea',
					  title: '制作梯度下降实验的实体模型',
  					  showImage: 'https://i.ibb.co/SJ1zFM4/image.jpg',
					  url: 'https://gitee.com/quanbinn/Learn-Mathematical-Olympiad-The-Interactive-Way/blob/master/chapters/%E5%BE%AE%E5%88%86/%E5%88%B6%E4%BD%9C%E6%A2%AF%E5%BA%A6%E4%B8%8B%E9%99%8D%E5%AE%9E%E9%AA%8C%E7%9A%84%E5%AE%9E%E4%BD%93%E6%A8%A1%E5%9E%8B.md',
					  tag: ['数学','深度学习'],
					  createdAt: 'Wed Sep 23 2020 17:22:29 GMT+0800 (中国标准时间)', // new Date()
					  creator: 'QwkSmTCZiw5KDx3L6'  // userId()	
					},
                  {   
					  _id: '860f191e979c19729de657ea',
					  title: '掷两个骰子试验',
  					  showImage: 'https://i.ibb.co/JcWYz49/image.jpg',
					  url: 'https://gitee.com/quanbinn/Learn-Mathematical-Olympiad-The-Interactive-Way/blob/master/chapters/%E6%A6%82%E7%8E%87/%E6%8E%B7%E4%B8%A4%E4%B8%AA%E9%AA%B0%E5%AD%90%E8%AF%95%E9%AA%8C.md',
					  tag: ['数学','机器学习'],
					  createdAt: 'Wed Oct 23 2020 20:22:29 GMT+0800 (中国标准时间)', // new Date()
					  creator: 'QwkSmTCZiw5KDx3L6'  // userId()	
				 }
      ]
    };
    await this.ctx.render('experiments/experiments.tpl', _data);
  }
}

module.exports = ExperimentsController;
```