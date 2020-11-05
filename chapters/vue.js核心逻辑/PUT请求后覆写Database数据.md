# PUT请求后覆写Database数据

## 打开实验文件

### 调试环境1：
单击右方的[vuejs-展示Data:第一个实验的标题 from tutorialspoint.com](http://tpcg.io/L9HHqh74)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

```javascript
<html>
    <head>
        <title>DDHuman.me</title>
        <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    </head>
    <body>        
        <div id="app" style="text-align:center;">
            <h1>{{ message }}</h1>
        </div>        
        <script type = "text/javascript">
          var app = new Vue({ 
            el: '#app',
            data: {
              message: '第一个实验的标题'
            }
          });
        </script>
    </body>
</html>
```

## Reference

1. [Vue.js：Introduction](https://vuejs.org/v2/guide/)
2. [Meteor: Todo App with Vue](https://www.meteor.com/tutorials/vue/components)
3. [Vue.js video on scrimba.com](https://scrimba.com/scrim/cQ3QVcr?pl=pXKqta)
