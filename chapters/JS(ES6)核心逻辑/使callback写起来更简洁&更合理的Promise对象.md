# 使callback写起来更简洁&更合理的Promise对象

## 打开实验文件

### 调试环境1：
单击右方的[在线代码段Url网址](http://www.pythontutor.com/visualize.html#mode=edit)，浏览器里会打开一个新的页面，把下面的这些html/js/css代码段分别拷贝到空白栏中。

### 调试环境2：
- 单机右方的[**JavaScript Demo from MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)，稍后在浏览器里会显示js的运行环境。
- 把下面的这些js代码段分别拷贝到的相应的文件空白栏中， 然后单击空白栏左下方的按键“Run”。

### 调试环境3：

- 单机右方的[Online Plunker](https://plnkr.co/edit/?open=lib%2Fscript.js)，稍后在浏览器里会显示js的运行环境。
- 把下面的这些html/js/css代码段分别拷贝到的相应的文件空白栏中， 然后单击右上方的按键“Preview”。


```javascript
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => resolve("done!"), 1000);
});

// resolve runs the first function in .then
promise.then(
  result => alert(result), // shows "done!" after 1 second
  error => alert(error) // doesn't run
);
```

```javascript
let promise = new Promise(function(resolve, reject) {
  setTimeout(() => reject(new Error("Whoops!")), 1000);
});

// reject runs the second function in .then
promise.then(
  result => alert(result), // doesn't run
  error => alert(error) // shows "Error: Whoops!" after 1 second
);
```

```javascript
new Promise((resolve, reject) => {
  setTimeout(() => resolve("result"), 2000)
})
  .finally(() => alert("Promise ready"))
  .then(result => alert(result)); // <-- .then handles the result
```

```javascript
new Promise((resolve, reject) => {
  throw new Error("error");
})
  .finally(() => alert("Promise ready"))
  .catch(err => alert(err));  // <-- .catch handles the error object
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
    showCircle(150, 150, 100).then(div => {
      div.classList.add('message-ball');
      div.append("Hello, world!");
    });
  }

  function showCircle(cx, cy, radius) {
    let div = document.createElement('div');
    div.style.width = 0;
    div.style.height = 0;
    div.style.left = cx + 'px';
    div.style.top = cy + 'px';
    div.className = 'circle';
    document.body.append(div);

    return new Promise(resolve => {
      setTimeout(() => {
        div.style.width = radius * 2 + 'px';
        div.style.height = radius * 2 + 'px';

        div.addEventListener('transitionend', function handler() {
          div.removeEventListener('transitionend', handler);
          resolve(div);
        });
      }, 0);
    })

/*
    setTimeout(() => {
      div.style.width = radius * 2 + 'px';
      div.style.height = radius * 2 + 'px';

      div.addEventListener('transitionend', function handler() {
        div.removeEventListener('transitionend', handler);
        callback(div);
      });
    }, 0);
*/

  }
  </script>


</body>
</html>
```

## Reference

1. [**Futures and promises** from wikipedia](https://en.wikipedia.org/wiki/Futures_and_promises)
2. [Introduction: callbacks](https://javascript.info/callbacks)
3. [Promise](https://javascript.info/promise-basics)
4. [Using Promises from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
5. [Promise from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
6. [Promise.prototype.then() from **MDN**](hhttps://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)
7. [**Promise 对象 from 阮一峰**](https://javascript.ruanyifeng.com/advanced/promise.html)
8. [**Promises chaining**](https://javascript.info/promise-chaining)






