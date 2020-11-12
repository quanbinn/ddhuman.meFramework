# showAnExperiment.vue

## 打开实验文件

单击右方的[experiment.vue](https://codepen.io/quanbinn/pen/ZEOqdLv), 浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。


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
              template: '<li>实验名称：{{ exp.title }}</li>'
            })

            var app = new Vue({
              el: '#app-exp',
              data: {
                experiments: [
                  {
					  _id: '860f191e810c87654de974bc',
					  title: '用橡皮筋和小塑料棍感受函数某点的切线',
					  url: 'https://gitee.com/quanbinn/Learn-Mathematical-Olympiad-The-Interactive-Way/blob/master/chapters/%E5%BE%AE%E5%88%86/%E7%94%A8%E6%A9%A1%E7%9A%AE%E7%AD%8B%E5%92%8C%E5%B0%8F%E5%A1%91%E6%96%99%E6%A3%8D%E6%84%9F%E5%8F%97%E5%87%BD%E6%95%B0%E6%9F%90%E7%82%B9%E7%9A%84%E5%88%87%E7%BA%BF.md',
					  tag: ['数学'],
					  createdAt: 'Wed Sep 30 2020 17:53:29 GMT+0800 (中国标准时间)', // new Date()
					  creator: 'QwkSmREWsw5KDx3L7'  // userId()	
                  },
                  {
					  _id: '860f191e810c19729de974ea',
					  title: '制作梯度下降实验的实体模型',
					  url: 'https://gitee.com/quanbinn/Learn-Mathematical-Olympiad-The-Interactive-Way/blob/master/chapters/%E5%BE%AE%E5%88%86/%E5%88%B6%E4%BD%9C%E6%A2%AF%E5%BA%A6%E4%B8%8B%E9%99%8D%E5%AE%9E%E9%AA%8C%E7%9A%84%E5%AE%9E%E4%BD%93%E6%A8%A1%E5%9E%8B.md',
					  tag: ['数学','深度学习'],
					  createdAt: 'Wed Sep 23 2020 17:22:29 GMT+0800 (中国标准时间)', // new Date()
					  creator: 'QwkSmTCZiw5KDx3L6'  // userId()	
					},
                  {   
					  _id: '860f191e979c19729de657ea',
					  title: '掷两个骰子试验',
					  url: 'https://gitee.com/quanbinn/Learn-Mathematical-Olympiad-The-Interactive-Way/blob/master/chapters/%E6%A6%82%E7%8E%87/%E6%8E%B7%E4%B8%A4%E4%B8%AA%E9%AA%B0%E5%AD%90%E8%AF%95%E9%AA%8C.md',
					  tag: ['数学','机器学习'],
					  createdAt: 'Wed Oct 23 2020 20:22:29 GMT+0800 (中国标准时间)', // new Date()
					  creator: 'QwkSmTCZiw5KDx3L6'  // userId()	
				 }
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

