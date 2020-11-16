# class的典型用法

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
'use strict';
class Clock {
  constructor({ template }) {this.template = template;}
  render() {
    let date = new Date();
    let hours = date.getHours();
    if (hours < 10) hours = '0' + hours;
    let mins = date.getMinutes();
    if (mins < 10) mins = '0' + mins;
    let secs = date.getSeconds();
    if (secs < 10) secs = '0' + secs;
    let output = this.template
      .replace('h', hours)
      .replace('m', mins)
      .replace('s', secs);
    console.log(output);
  }
  stop() {clearInterval(this.timer);}
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

## Reference

1. [**Class basic syntax**](https://javascript.info/class)
2. [**Class inheritance**](https://javascript.info/class-inheritance)



