# 让函数表达式看起来更简洁的=>写法(Arrow functions)

## ES6的写法

单击右方的[在线代码段Url网址](http://pythontutor.com/visualize.html#code=let%20weightVar,%20heightVar,%20BMIFloat,%20BMI%3B%20%20%20%20%0A%0Alet%20%20myBMI%20%3D%20%28weightArgu,%20heightArgu%29%20%3D%3E%20%7B%20%20%20%0A%20%20%20%20weightVar%20%3D%20weightArgu%3B%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20heightVar%20%3D%20heightArgu%3B%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20BMIFloat%20%3D%20weightVar%20/%20%28heightVar%20*%20heightVar%29%3B%20%0A%20%20%20%20BMI%20%3D%20BMIFloat.toFixed%281%29%3B%20%20%20%20%0A%0A%20%20%20%20return%20BMI%3B%0A%7D%0A%0Aconsole.log%28%22My%20BMI%20is%20%22%20%2B%20myBMI%2870,%201.745%29%20%2B%20%22.%22%29%3B&cumulative=false&curInstr=0&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
let weightVar, heightVar, BMIFloat, BMI;    

let  myBMI = (weightArgu, heightArgu) => {   
    weightVar = weightArgu;          
    heightVar = heightArgu;        

    BMIFloat = weightVar / (heightVar * heightVar); 
    BMI = BMIFloat.toFixed(1);    

    return BMI;
}

console.log("My BMI is " + myBMI(70, 1.745) + ".");
```

## ES6之前的写法

```javascript
var weightVar, heightVar, BMIFloat, BMI;    

function myBMI (weightArgu, heightArgu) {   
    weightVar = weightArgu;          
    heightVar = heightArgu;        

    BMIFloat = weightVar / (heightVar * heightVar); 
    BMI = BMIFloat.toFixed(1);    

    return BMI;
}

console.log("My BMI is " + myBMI(63.5, 1.74) + ".");
```

## Reference

1. [Arrow (computer science)](https://en.wikipedia.org/wiki/Arrow_(computer_science))
2. [Arrow function expressions from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
3. [**Arrow functions, the basics**](https://javascript.info/arrow-functions-basics)
4. [**BABEL:Try it out**](https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&spec=false&loose=false&code_lz=Q&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=env%2Creact%2Cstage-2%2Cenv&prettier=false&targets=&version=7.11.6&externalPlugins=)



