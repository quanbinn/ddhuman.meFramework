# 让函数表达式看起来更简洁的=>写法(Arrow functions)

## ES6的写法

单击右方的[在线代码段Url网址](http://pythontutor.com/visualize.html#code=let%20%20myBMI%20%3D%20%28weight,%20height%29%20%3D%3E%20%7B%20%20%20%0A%20%20%20%20let%20BMI%20%3D%20%28weight%20/%20%28height%20*%20height%29%29.toFixed%281%29%3B%20%0A%20%20%20%20return%20BMI%3B%0A%7D%0A%0Aconsole.log%28%22My%20BMI%20is%20%22%20%2B%20myBMI%2870,%201.745%29%20%2B%20%22.%22%29%3B&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
let  myBMI = (weight, height) => {   
    let BMI = (weight / (height * height)).toFixed(1); 
    return BMI;
}

console.log("My BMI is " + myBMI(70, 1.745) + ".");
```

## ES6之前的写法

```javascript
function myBMI (weight, height) {   
    let BMI = (weight / (height * height)).toFixed(1); 
    return BMI;
}

console.log("My BMI is " + myBMI(70, 1.745) + ".");
```

## Reference

1. [Arrow (computer science)](https://en.wikipedia.org/wiki/Arrow_(computer_science))
2. [Arrow function expressions from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
3. [**Arrow functions, the basics**](https://javascript.info/arrow-functions-basics)
4. [**BABEL:Try it out**](https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&spec=false&loose=false&code_lz=Q&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=env%2Creact%2Cstage-2%2Cenv&prettier=false&targets=&version=7.11.6&externalPlugins=)



