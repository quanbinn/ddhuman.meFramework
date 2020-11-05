# DELETE请求后删除Database数据

## 打开实验文件

单击右方的[Delete handle user input into Database](http://tpcg.io/hoNsdjlR)，浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

```javascript
<html>
    <head>
        <title>DDHuman.me</title>
        <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    </head>
    <body>        
        <div id="app-5">
          <p>{{ message }}</p>
          <button v-on:click="deleteExperiment">delete the experiment document</button>
        </div>  
        <script type = "text/javascript">
          var app5 = new Vue({
            el: '#app-5',
            data: {
              message: 'delete the experiment document'
            },
            methods: {
              deleteExperiment: function () {
                alert("delete the experiment document by ID in the database!");
              }
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

