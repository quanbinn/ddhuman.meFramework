# 调用子文件中类和函数的module功能

单击右方的[在线代码段Url网址](https://plnkr.co/edit/oFvtBUjmI2z96MSr?open=lib%2Fscript.js&preview)，浏览器里会打开一个新的页面，里面有可以在线运行的项目文件。

## index.html
```html
<!doctype html>
<script type="module" src="exportBMI.js"></script>
```

## exportBMI.js
```javascript
import {myBMI} from './modules/calculateBMI.js';

let height = 1.745;
let weight = 70;
   
let BMI = myBMI(weight, height);  

document.body.innerHTML = "你的BMI是：" + myBMI(weight, height); 
```

## ./modules/calculateBMI.js
```javascript
let myBMI = (weightArgu, heightArgu) => {   
    let weightVar = weightArgu;          
    let heightVar = heightArgu;        
    let BMIFloat = weightVar / (heightVar * heightVar); 
    let BMI = BMIFloat.toFixed(1);    
    return BMI;
}

export { myBMI };
```

## Reference

1. [JavaScript modules from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
2. [**Modules, introduction**](https://javascript.info/modules-intro)



