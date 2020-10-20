# 在1个函数中把另外1个函数作为参数调用的callback

## 打开实验文件

### 调试环境1：
单击右方的[在线代码段Url网址](http://www.pythontutor.com/visualize.html#mode=edit)，浏览器里会打开一个新的页面，把下面的这些html/js/css代码段分别拷贝到空白栏中。

### 调试环境2：
- 单机右方的[Online Plunker](https://plnkr.co/edit/?open=lib%2Fscript.js)，稍后在浏览器里会显示js的运行环境。
- 把下面的这些html/js/css代码段分别拷贝到的相应的文件空白栏中， 然后单击右上方的按键“Preview”。

```javascript
function doSomething(msg, callback){
     console.log(msg);
    if(typeof callback == "function") 
    callback();
 } 
doSomething("回调函数", function(){
    console.log("匿名函数实现回调!");
 }); 
```

```javascript
var p_client = new Db('integration_tests_20', new Server("127.0.0.1", 27017, {}), {'pk':CustomPKFactory});
   p_client.open(function(err, p_client) {
       p_client.dropDatabase(function(err, done) {
           p_client.createCollection('test_custom_key', function(err, collection) {
               collection.insert({'a':1}, function(err, docs) {
                   collection.find({'_id':new ObjectID("aaaaaaaaaaaa")}, function(err, cursor) {
                       cursor.toArray(function(err, items) {
                           test.assertEquals(1, items.length);
 
                           // Let's close the db
                           p_client.close();
                       });
                   });
               });
           });
       });
   });
```

```html
<!DOCTYPE html>
<script>
'use strict';

function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;
  script.onload = () => callback(script);
  document.head.append(script);
}

loadScript('https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js', script => {
  alert(`Cool, the script ${script.src} is loaded`);
  alert( _ ); // function declared in the loaded script
});
</script>
```

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <style>
    .message-ball {
      font-size: 20px;
      line-height: 200px;
      text-align: center;
    }
    .circle {
      transition-property: width, height, margin-left, margin-top;
      transition-duration: 2s;
      position: fixed;
      transform: translateX(-50%) translateY(-50%);
      background-color: red;
      border-radius: 50%;
    }
  </style>
</head>

<body>

  <button onclick="go()">Click me</button>

  <script>

  function go() {
    showCircle(150, 150, 100, div => {
      div.classList.add('message-ball');
      div.append("Hello, world!");
    });
  }

  function showCircle(cx, cy, radius, callback) {
    let div = document.createElement('div');
    div.style.width = 0;
    div.style.height = 0;
    div.style.left = cx + 'px';
    div.style.top = cy + 'px';
    div.className = 'circle';
    document.body.append(div);

    setTimeout(() => {
      div.style.width = radius * 2 + 'px';
      div.style.height = radius * 2 + 'px';

      div.addEventListener('transitionend', function handler() {
        div.removeEventListener('transitionend', handler);
        callback(div);
      });
    }, 0);
  }
  </script>

</body>
</html>
```

## Reference

1. [**Futures and promises** from wikipedia](https://en.wikipedia.org/wiki/Futures_and_promises)
2. [Introduction: callbacks](https://javascript.info/callbacks)
3. [Promise](https://javascript.info/promise-basics)
4. [Promise from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)




