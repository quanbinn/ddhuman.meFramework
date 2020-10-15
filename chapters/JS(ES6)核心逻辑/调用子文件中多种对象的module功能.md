# 调用子文件中类和函数的module功能

单击右方的[在线代码段Url网址](https://plnkr.co/edit/oFvtBUjmI2z96MSr?open=lib%2Fscript.js&preview)，浏览器里会打开一个新的页面，里面有可以在线运行的项目文件。

## index.html
```html
<!doctype html>
<script type="module" src="exportBMI.js"></script>
```

## exportBMI.js
```javascript
import {myBMI, minWeight, maxWeight} from './modules/calculateBMI.js';

let height = 1.745;
let weight = 70;

let BMI = myBMI(weight, height);
let min = minWeight(weight, height);
let max = maxWeight(weight, height);

if (BMI < 18.5) {
  alert("你的BMI是"+ BMI + "。\n你的体重过轻。"); 
  alert("你的正常体重应该在:"+min+"-"+max+"公斤的范围内。");
} else if (BMI >= 18.5 && BMI < 24.0) {
  alert("你的BMI是"+ BMI + "。\n你的体重正常。"); 
  alert("你的正常体重应该在:"+min+"-"+max+"公斤的范围内。"); 
} else if (BMI >= 24.0 && BMI < 28.0) {
  alert("你的BMI是"+ BMI + "。\n你的体重超重。"); 
  alert("你的正常体重应该在:"+min+"-"+max+"公斤的范围内。"); 
} else {
  alert("你的BMI是"+ BMI + "。\n你的体重肥胖。"); 
  alert("你的正常体重应该在:"+min+"-"+max+"公斤的范围内。"); 
}

document.body.innerHTML = "你的BMI是：" + BMI+ "。 " + "你的正常体重应该在:"+ min + "-"+ max+"公斤的范围内。"; 
```

## ./modules/calculateBMI.js
```javascript
let  myBMI = (weight, height) => {   
    let BMI = (weight / (height * height)).toFixed(1); 
    return BMI;
}

let minWeight =  (weight, height) =>{
	return (height * height * 18.5).toFixed(1);
}  

let maxWeight =  (weight, height) =>{
	return (height * height * 24.0).toFixed(1);
}  

export { myBMI, minWeight, maxWeight };
```

## Reference

1. [JavaScript modules from **MDN**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
2. [**Modules, introduction**](https://javascript.info/modules-intro)



