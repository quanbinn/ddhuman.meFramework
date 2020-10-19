# 使用python在线体验多进程

## 打开实验文件

- 单机右方的[Online Python](https://www.online-python.com)，稍后在浏览器里会显示Python的运行环境。
- 把下面的这些python代码段分别拷贝到main.py的空白栏中， 然后单击左下方的按键“Run”。



单击右方的[在线代码段Url网址](http://pythontutor.com/visualize.html#code=import%20threading%0Aimport%20time%0Adef%20func1%28x,%20y%29%3A%0A%20%20%20%20for%20i%20in%20range%28x,%20y%29%3A%0A%20%20%20%20%20%20%20%20print%28i,%20end%3D'%20'%29%0A%20%20%20%20%23time.sleep%2810%29%0A%0At1%3Dthreading.Thread%28target%20%3D%20func1,%20args%20%3D%20%2815,%2020%29%29%0At1.start%28%29%0At1.join%285%29%0At2%3Dthreading.Thread%28target%20%3D%20func1,%20args%20%3D%20%285,%2010%29%29%0At2.start%28%29%0A%23t2.join%28%29%20%23the%20program%20will%20not%20continue%20until%20t2%20thread%20finishs%0A%0Aprint%28t1.isAlive%28%29%29%0Atime.sleep%282%29%20%23try%20to%20comment%20this%20line%20to%20see%20the%20different%20result%0Aprint%28t2.isAlive%28%29%29%0A&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=py3anaconda&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。



#### 创建多进程

```python
from multiprocessing import Process
import os

def f(name):
    print('module name:', __name__)
    print('parent process:', os.getppid())
    print('process id:', os.getpid())
    print('hello', name)

if __name__ == '__main__':
    p = Process(target=f, args=('bob',))
    p.start()
    p.join()
```



## Reference

1. [**Futures and promises** from wikipedia](https://en.wikipedia.org/wiki/Futures_and_promises)
2. [Introduction: callbacks](https://javascript.info/callbacks)
3. [Promise](https://javascript.info/promise-basics)
4. [Async/await](https://javascript.info/async-await)
5. [Promise from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
6. [async function from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
7. [Making asynchronous programming easier with async and await from **MDN**](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await)




