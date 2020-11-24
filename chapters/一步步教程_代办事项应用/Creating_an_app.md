# Creating an app

1. **安装比较新版本的nodejs和npm (egg.js要求npm >=6.1.0)**，例如安装Node.js v14.x版本的过程如下：
```bash
$ sudo apt-get install curl
$ curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
$ sudo apt-get install nodejs
```

2. 
```bash
$ mkdir ddhumanme && cd ddhumanme
```

3. 
```bash
$ npm init egg --type=simple
```

4. 
```bash
$ npm install
```

5. 
```bash
$ npm run dev
```

6. 在浏览器里输入： http://localhost:7001

## Reference

1. [eggjs.org快速入门](https://eggjs.org/zh-cn/intro/quickstart.html)
2. [How to Install Latest Node.js on Ubuntu with Apt-Get](https://tecadmin.net/install-latest-nodejs-npm-on-ubuntu/)
3. [**NodeSource Node.js Binary Distributions**](https://github.com/nodesource/distributions/blob/master/README.md)


