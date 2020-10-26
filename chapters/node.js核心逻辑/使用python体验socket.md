# 使用python体验socket

## 打开实验文件

### 调试环境：
- 单机右方的[Online Python](https://www.online-python.com)，稍后在浏览器里会显示Python的运行环境。
- 把下面的这些python代码段分别拷贝到main.py的空白栏中， 然后单击左下方的按键“Run”。

### client.py
```python
import socket

HOST = '127.0.0.1'          #服务端主机IP地址
PORT = 50007                #服务端主机端口号
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((HOST, PORT))     #连接连接
while True:
    c = input('Input the content you want to send:')
    s.sendall(c.encode())   #发送数据
    data = s.recv(1024)     #从客户端接收数据
    data = data.decode()
    print('Received:', data)
    if c.lower() == 'bye':
        break
s.close()                   #关闭连接
```

### getIP_MAC.py
```python
import socket
import uuid

ip = socket.gethostbyname(socket.gethostname())
node = uuid.getnode()
macHex = uuid.UUID(int=node).hex[-12:]
mac = []
for i in range(len(macHex))[::2]:
    mac.append(macHex[i:i+2])
mac = ':'.join(mac)
print('IP:', ip)
print('MAC:', mac)
```

### port_scan.py
```python
import socket
import multiprocessing

def ports(ports_service):
    #获取常用端口对应的服务名称
    for port in list(range(1,100))+[143,145,113,443,445,3389, 8080]:
        try:
            ports_service[port] = socket.getservbyport(port)
        except socket.error:
            pass

def ports_scan(host, ports_service):
    ports_open = []
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(0.1)
    except socket.error:
        print('socket creation error')
        sys.exit()
    for port in ports_service:
        try:
            #尝试连接指定端口
            sock.connect((host,port))
            #记录打开的端口
            ports_open.append(port)
            sock.close()
        except socket.error:
            pass
    return ports_open

if __name__=='__main__':
    m = multiprocessing.Manager()
    ports_service = dict()
    results = dict()
    ports(ports_service)
    #创建进程池，允许最多8个进程同时运行
    pool = multiprocessing.Pool(processes=8)
    net = '10.2.1.'
    for host_number in map(str,range(8,10)):
        host = net+host_number
        #创建一个新进程，同时记录其运行结果
        results[host] = pool.apply_async(ports_scan, (host, ports_service))
        print('starting '+host+'...')
    #关闭进程池，close()必须在join()之前调用
    pool.close()
    #等待进程池中的进程全部执行结束
    pool.join()

    #打印输出结果
    for host in results:
        print('='*30)
        print(host,'.'*10)
        for port in results[host].get():
            print(port, ':', ports_service[port])
```

### sender.py
```python
import socket
import sys

s=socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.sendto(sys.argv[1].encode() , ("192.168.0.103" ,5000))#假设192.168.0.103是接收端机器的IP地址
s.close( )
```

### sockMiddle.py
```python
import sys
import socket
import threading

def middle(conn, addr):
    #面向服务器的Socket
    sockDst = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sockDst.connect((ipServer,portServer))
    while True:
        data = conn.recv(1024).decode()
        print('收到客户端消息：'+data)
        if data == '不要发给服务器':
            conn.send('该消息已被代理服务器过滤'.encode())
            print('该消息已过滤')
        elif data.lower() == 'bye':
            print(str(addr)+'客户端关闭连接')
            break
        else:
            sockDst.send(data.encode())
            print('已转发服务器')
            data_fromServer = sockDst.recv(1024).decode()
            print('收到服务器回复的消息：'+data_fromServer)
            if data_fromServer == '不要发给客户端':
                conn.send('该消息已被代理服务器修改'.encode())
                print('消息已被篡改')
            else:
                conn.send(b'Server reply:'+data_fromServer.encode())
                print('已转发服务器消息给客户端')
        
    conn.close()
    sockDst.close()

def main():
    sockScr = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sockScr.bind(('', portScr))
    sockScr.listen(200)
    print('代理已启动')
    while True:
        try:
            conn, addr = sockScr.accept()
            t = threading.Thread(target=middle, args=(conn, addr))
            t.start()
            print('新客户：'+str(addr))
        except:
            pass
        
if __name__ == '__main__':
    try:
        #(本机IP地址,portScr)<==>(ipServer,portServer)
        #代理服务器监听端口
        portScr = int(sys.argv[1])
        #服务器IP地址与端口号
        ipServer = sys.argv[2]
        portServer = int(sys.argv[3])
        main()
    except:
        print('Sth error')
```

### sockMiddle_server.py
```python
import sys
import socket
import threading

#回复消息，原样返回
def replyMessage(conn):
    while True:
        data = conn.recv(1024)
        conn.send(data)
        if data.decode().lower() == 'bye':
            break
    conn.close()

def main():
    sockScr = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sockScr.bind(('', port))
    sockScr.listen(200)
    while True:
        try:
            conn, addr = sockScr.accept()
            #只允许特定主机访问本服务器
            if addr[0] != onlyYou:
                conn.close()
                continue
            #创建并启动线程
            t = threading.Thread(target=replyMessage, args=(conn,))
            t.start()        
        except:
            print('error')

if __name__ == '__main__':
    try:
        #获取命令行参数
        port = int(sys.argv[1])
        onlyYou = sys.argv[2]
        main()
    except:
        print('Must give me a number as port')        
```

## Reference

1. [Network socket](https://en.wikipedia.org/wiki/Network_socket)
2. [Unix domain socket](https://en.wikipedia.org/wiki/Unix_domain_socket)
3. 董付国.[Python可以这样学](http://product.dangdang.com/24180463.html).第10章:网络程序设计.




