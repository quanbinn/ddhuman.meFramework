# 从Database取得数据通过Template Render 成html文件

## 打开实验文件

单击右方的[Using template render to html](http://tpcg.io/4HfWXgAf)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

```javascript
<html>
    <head>
        <title>DDHuman.me</title>
        <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    </head>
    <body>        
        <div id="app-exp">
          <ol>
            <specfic-exp
              v-for="exp in experiments"
              v-bind:exp="exp"
              v-bind:key="exp._id"
            ></specfic-exp>
          </ol>
        </div>
        <script type = "text/javascript">
            Vue.component('specfic-exp', {
              props: ['exp'],
              template: '<li>实验名称：{{ exp.title }}</li><li>实验步骤地址：{{ exp.url }}</li>'
            })

            var app = new Vue({
              el: '#app-exp',
              data: {
                experiments: [
                  {
                    _id: '860f191e810c19729de974ea',
                    title: '制作梯度下降实验的实体模型',
                    url: 'https://gitee.com/quanbinn/Learn-Mathematical-Olympiad-The-Interactive-Way/blob/master/chapters/%E5%BE%AE%E5%88%86/%E5%88%B6%E4%BD%9C%E6%A2%AF%E5%BA%A6%E4%B8%8B%E9%99%8D%E5%AE%9E%E9%AA%8C%E7%9A%84%E5%AE%9E%E4%BD%93%E6%A8%A1%E5%9E%8B.md',
                    tag: ['数学','深度学习','机器学习'],
                    createdAt: 'Wed Sep 23 2020 17:22:29 GMT+0800 (中国标准时间)', // new Date()
                    creator: 'QwkSmTCZiw5KDx3L6'  // userId()	
                  },
                  { id: 1, text: 'Cheese' },
                  { id: 2, text: 'Whatever else humans are supposed to eat' }
                ]
              }
            })
        </script>
    </body>
</html>
```

## Reference

1. [Vue.js：Introduction](https://vuejs.org/v2/guide/)
2. [Meteor: Todo App with Vue](https://www.meteor.com/tutorials/vue/components)
3. [Vue.js video on scrimba.com](https://scrimba.com/scrim/cQ3QVcr?pl=pXKqta)

