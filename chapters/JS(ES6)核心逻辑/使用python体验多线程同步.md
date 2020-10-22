# 使用python在线体验多线程同步

## 打开实验文件

### 调试环境1：
单击右方的[在线代码段Url网址](http://www.pythontutor.com/visualize.html#mode=edit)，浏览器里会打开一个新的页面，把下面的这些python代码段分别拷贝到空白栏中。

### 调试环境2：
- 单机右方的[Online Python](https://www.online-python.com)，稍后在浏览器里会显示Python的运行环境。
- 把下面的这些python代码段分别拷贝到main.py的空白栏中， 然后单击左下方的按键“Run”。

#### Thread Synchronization Using Queue
```python
import threading
import time
import queue

class Producer(threading.Thread):
    def __init__(self, threadname):
        threading.Thread.__init__(self, name = threadname)
    def run(self):
        global myqueue
        myqueue.put(self.getName())
        print(self.getName(), ' put ', self.getName(), ' to queue.')

class Consumer(threading.Thread):
    def __init__(self, threadname):
        threading.Thread.__init__(self, name = threadname)
    def run(self):
        global myqueue        
        print(self.getName(), ' get ', myqueue.get(), ' from queue.')

myqueue = queue.Queue()
plist = []
clist = []

for i in range(10):
    p = Producer('Producer' + str(i))
    plist.append(p)
    c = Consumer('Consumer' + str(i))
    clist.append(c)

for i in plist:
    i.start()
    i.join()
for i in clist:
    i.start()
    i.join()
```

#### Thread Synchronization Using Event
```python
import threading
class mythread(threading.Thread):
    def __init__(self, threadname):
        threading.Thread.__init__(self, name = threadname)
    def run(self):
        global myevent
        if myevent.isSet():
            myevent.clear()
            myevent.wait()
            print(self.getName())
        else:
            print(self.getName())
            myevent.set()

myevent = threading.Event()
myevent.set()
tl = []
for i in range(10):
    t = mythread(str(i))
    tl.append(t)

for i in tl:
    i.start()
```

#### Thread Synchronization Using Condition
```python
import threading

class Producer(threading.Thread):
    def __init__(self, threadname):
        threading.Thread.__init__(self,name=threadname)
    def run(self):
        global x
        con.acquire()
        if x == 20:
            con.wait()
        else:
            print('\nProducer:', end=' ')
            for i in range(20):                
                print(x, end=' ')
                x = x + 1
            print(x)
            con.notify()
        con.release()

class Consumer(threading.Thread):
    def __init__(self, threadname):
        threading.Thread.__init__(self, name =threadname)
    def run(self):
        global x
        con.acquire()
        if x == 0:
            con.wait()
        else:
            print('\nConsumer:', end=' ')
            for i in range(20):                
                print (x, end=' ')
                x = x - 1
            print(x)
            con.notify()
        con.release()

con = threading.Condition()
x = 0
p = Producer('Producer')
c = Consumer('Consumer')
p.start()
c.start()
p.join()
c.join()
print('\nAfter Producer and Consumer all done:',x)
```

#### Thread Synchronization Using Lock
```python
import threading
import time
class mythread(threading.Thread):
    
    def __init__(self):
        threading.Thread.__init__(self)
        
    def run(self):
        global x
        lock.acquire()
        for i in range(3):
            x = x + i
        time.sleep(2)
        print(x)
        lock.release()

#lock = threading.Lock()
lock = threading.RLock()
tl = []
for i in range(10):
    t = mythread()
    tl.append(t)

x = 0

for i in tl:
    i.start()
```

## Reference

1. 董付国.[Python可以这样学](http://product.dangdang.com/24180463.html).第13章:多线程与多进程编程.




