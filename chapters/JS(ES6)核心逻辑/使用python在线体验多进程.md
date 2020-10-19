# 使用python在线体验多进程

## 打开实验文件

### 调试环境1：
单击右方的[在线代码段Url网址](http://www.pythontutor.com/visualize.html#mode=edit)，浏览器里会打开一个新的页面，把下面的这些python代码段分别拷贝到空白栏中。

### 调试环境2：
- 单机右方的[Online Python](https://www.online-python.com)，稍后在浏览器里会显示Python的运行环境。
- 把下面的这些python代码段分别拷贝到main.py的空白栏中， 然后单击左下方的按键“Run”。

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

```python
from multiprocessing import Pool
from statistics import mean

def f(x):
    return mean(x)

if __name__ == '__main__':
    x = [list(range(10)), list(range(20,30)), list(range(50,60)), list(range(80,90))]
    with Pool(5) as p:
        print(p.map(f, [x[0], x[1], x[2], x[3]]))
```

```python
import multiprocessing as mp

def foo(q):
    q.put('hello world!')

if __name__ == '__main__':
    mp.set_start_method('spawn')
    q = mp.Queue()
    p = mp.Process(target=foo, args=(q,))
    p.start()
    p.join()
    print(q.get())
```

```python
from multiprocessing import Process, Pipe

def f(conn):
    conn.send('hello world')
    conn.close()

if __name__ == '__main__':
    parent_conn, child_conn = Pipe()
    p = Process(target=f, args=(child_conn,))
    p.start()
    print(parent_conn.recv())
    p.join()
```

```python
from multiprocessing import Process, Manager

def f(d, l, t):
    d['name'] = 'Dong Fuguo'
    d['age'] = 38
    d['sex'] = 'Male'
    d['affiliation'] = 'SDIBT'
    l.reverse()
    t.value = 3
    

if __name__ == '__main__':
    with Manager() as manager:
        d = manager.dict()
        l = manager.list(range(10))
        t = manager.Value('i', 0)

        p = Process(target=f, args=(d, l, t))
        p.start()
        p.join()

        for item in d.items():
            print(item)
        print(l)
        print(t.value)
```

```python
from multiprocessing import Process, Event

def f(e, i):
    if e.is_set():
        e.wait()
        print('hello world', i)
        e.clear()
    else:
        e.set()

if __name__ == '__main__':
    e = Event()

    for num in range(10):
        Process(target=f, args=(e,num)).start()
```

## Reference

1. 董付国.[Python可以这样学](http://product.dangdang.com/24180463.html).第13章:多线程与多进程编程.




