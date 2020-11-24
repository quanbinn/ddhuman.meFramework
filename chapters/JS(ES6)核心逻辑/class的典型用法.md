# class的典型用法

## 核心逻辑

### javascript中Class里面的this (等同于python中Class里面的self)可以被理解为一组key和value的集合, 即this = {key1: value1, key2: value2, key3: value3 ...}, 表达的意义是property1: value1, property2: value2, property3: value3; ... . 

单击右方的[在线代码段Url网址](http://pythontutor.com/visualize.html#code='use%20strict'%3B%0Aclass%20User%20%7B%0A%20%20constructor%28name%29%20%7B%0A%20%20%20%20//%20invokes%20the%20setter%0A%20%20%20%20this.name%20%3D%20name%3B%0A%20%20%7D%0A%20%20get%20name%28%29%20%7Breturn%20this._name%3B%7D%0A%20%20set%20name%28value%29%20%7B%0A%20%20%20%20if%20%28value.length%20%3C%204%29%20%7B%0A%20%20%20%20%20%20console.log%28value%29%3B%0A%20%20%20%20%20%20console.log%28%22Name%20is%20too%20short.%22%29%3B%0A%20%20%20%20%20%20return%3B%0A%20%20%20%20%7D%0A%20%20%20%20this._name%20%3D%20value%3B%0A%20%20%7D%0A%7D%0A%0Alet%20user%20%3D%20new%20User%28%22xia%22%29%3B%0Aconsole.log%28user.name%29%3B%20//%20John%0Auser%20%3D%20new%20User%28%22%22%29%3B%20//%20Name%20is%20too%20short.&cumulative=false&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
'use strict';
class User {
  constructor(name) {
    // invokes the setter
    this.name = name;
  }
  get name() {return this._name;}
  set name(value) {
    if (value.length < 4) {
      console.log(value);
      console.log("Name is too short.");
      return;
    }
    this._name = value;
  }
}

let user = new User("xia");
console.log(user.name); // John
user = new User(""); // Name is too short.
```

单击右方的[在线代码段Url网址](http://pythontutor.com/visualize.html#code='use%20strict'%3B%0Aclass%20Animal%20%7B%0A%20%20constructor%28name%29%20%7B%0A%20%20%20%20this.name%20%3D%20name%3B%0A%20%20%20%20console.log%28this%29%3B%0A%20%20%7D%0A%7D%0A%0Aclass%20Rabbit%20extends%20Animal%20%7B%0A%20%20constructor%28name%29%20%7B%0A%20%20%20%20//console.log%28this%29%3B%0A%20%20%20%20super%28name%29%3B%0A%20%20%20%20console.log%28this%29%3B%0A%20%20%20%20this.created%20%3D%20Date.now%28%29%3B%0A%20%20%20%20console.log%28this%29%3B%0A%20%20%7D%0A%7D%0A%0Alet%20rabbit%20%3D%20new%20Rabbit%28%22White%20Rabbit%22%29%3B%20//%20ok%20now%0Aconsole.log%28rabbit%29%3B%0Aconsole.log%28rabbit.name%29%3B%20//%20White%20Rabbit&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
'use strict';
class Animal {
  constructor(name) {
    this.name = name;
    console.log(this);
  }
}

class Rabbit extends Animal {
  constructor(name) {
    //console.log(this);
    super(name);
    console.log(this);
    this.created = Date.now();
    console.log(this);
  }
}

let rabbit = new Rabbit("White Rabbit"); // ok now
console.log(rabbit);
console.log(rabbit.name); // White Rabbit
```

```javascript
class Animal {
  constructor(name) {
    this.speed = 0;
    this.name = name;
  }
}

class Rabbit extends Animal {
  constructor(speed, name, earLength) {
    super(speed, name);
    this.earLength = earLength;
  }
}

// now fine
let rabbit = new Rabbit(5, "White Rabbit", 10);
console.log(rabbit.name); // White Rabbit
console.log(rabbit.earLength); // 10
console.log(rabbit.speed); // 10
```

```javascript
class Animal {
  constructor(name) {
    this.speed = 0;
    this.name = name;
  }
  run(speed) {
    this.speed = speed;
    console.log(`${this.name} runs with speed ${this.speed}.`);
    console.log(this);
  }
  stop() {
    this.speed = 0;
    console.log(`${this.name} stands still.`);
    console.log(this);
  }
}
class Rabbit extends Animal {
  hide() {console.log(`${this.name} hides!`);}
  stop() {
    super.stop(); // call parent stop
    this.hide(); // and then hide
    console.log(this);
  }
}
let rabbit = new Rabbit("White Rabbit");
rabbit.run(5); // White Rabbit runs with speed 5.
rabbit.stop(); // White Rabbit stands still. White rabbit hides!
```

### 打开浏览器(例如Chrome), 首先在渲染后的网页的任何一个位置右击，弹出一个菜单; 然后右击最后一项“检查”, 在出现的界面的左上角左击Console, 把下面的代码段粘贴到空白的输入界面中，按下“Enter”键运行这段代码。

```javascript
class Clock {
  constructor({ template }) {
    this.template = template;
  }

  render() {
    let date = new Date();
    let hours = date.getHours(); if (hours < 10) hours = '0' + hours;
    let mins = date.getMinutes(); if (mins < 10) mins = '0' + mins;
    let secs = date.getSeconds(); if (secs < 10) secs = '0' + secs;
    let output = this.template
      .replace('h', hours)
      .replace('m', mins)
      .replace('s', secs);
    console.log(output);
  }

  stop() {
    clearInterval(this.timer);
  }

  start() {
    this.render();
    this.timer = setInterval(() => this.render(), 1000);
  }
}

class ExtendedClock extends Clock {
  constructor(options) {
    super(options);
    let { precision = 1000 } = options;
    this.precision = precision;
  }

  start() {
    this.render();
    this.timer = setInterval(() => this.render(), this.precision);
  }
};

let lowResolutionClock = new ExtendedClock({
  template: 'h:m:s',
  precision: 10000
});

lowResolutionClock.start();
```

### 单击右方的[在线代码段Url网址](http://www.pythontutor.com/visualize.html#code=class%20Clock%20%7B%0A%20%20constructor%28%7B%20template%20%7D%29%20%7Bthis.template%20%3D%20template%3B%7D%0A%20%20render%28%29%20%7B%0A%20%20%20%20let%20date%20%3D%20new%20Date%28%29%3B%0A%20%20%20%20let%20hours%20%3D%20date.getHours%28%29%3B%20if%20%28hours%20%3C%2010%29%20hours%20%3D%20'0'%20%2B%20hours%3B%0A%20%20%20%20let%20mins%20%3D%20date.getMinutes%28%29%3B%20if%20%28mins%20%3C%2010%29%20mins%20%3D%20'0'%20%2B%20mins%3B%0A%20%20%20%20let%20secs%20%3D%20date.getSeconds%28%29%3B%20if%20%28secs%20%3C%2010%29%20secs%20%3D%20'0'%20%2B%20secs%3B%0A%20%20%20%20let%20output%20%3D%20this.template%0A%20%20%20%20%20%20.replace%28'h',%20hours%29%0A%20%20%20%20%20%20.replace%28'm',%20mins%29%0A%20%20%20%20%20%20.replace%28's',%20secs%29%3B%0A%20%20%20%20console.log%28output%29%3B%0A%20%20%20%20%7D%0A%20%20start%28%29%20%7Bthis.render%28%29%3B%7D%0A%7D%0Aclass%20ExtendedClock%20extends%20Clock%20%7B%0A%20%20constructor%28options%29%20%7B%0A%20%20%20%20super%28options%29%3B%0A%20%20%20%20let%20%7B%20precision%20%3D%201000%20%7D%20%3D%20options%3B%0A%20%20%20%20this.precision%20%3D%20precision%3B%0A%20%20%7D%0A%20%20start%28%29%20%7Bthis.render%28%29%3Bconsole.log%28this.precision%29%3B%7D%0A%7D%3B%0Alet%20lowResolutionClock%20%3D%20new%20ExtendedClock%28%7Btemplate%3A%20'h%3Am%3As',precision%3A%2010000%7D%29%3B%0AlowResolutionClock.start%28%29%3B&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
class Clock {
  constructor({ template }) {this.template = template;}
  render() {
    let date = new Date();
    let hours = date.getHours(); if (hours < 10) hours = '0' + hours;
    let mins = date.getMinutes(); if (mins < 10) mins = '0' + mins;
    let secs = date.getSeconds(); if (secs < 10) secs = '0' + secs;
    let output = this.template
      .replace('h', hours)
      .replace('m', mins)
      .replace('s', secs);
    console.log(output);
    }
  start() {this.render();}
}
class ExtendedClock extends Clock {
  constructor(options) {
    super(options);
    let { precision = 1000 } = options;
    this.precision = precision;
  }
  start() {this.render();console.log(this.precision);}
};
let lowResolutionClock = new ExtendedClock({template: 'h:m:s',precision: 10000});
lowResolutionClock.start();
```

## Reference

1. [Class (programming) from wikipedia](https://simple.wikipedia.org/wiki/Class_(programming))
2. [**Class basic syntax**](https://javascript.info/class)
3. [**Class inheritance**](https://javascript.info/class-inheritance)
4. [super](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super)



