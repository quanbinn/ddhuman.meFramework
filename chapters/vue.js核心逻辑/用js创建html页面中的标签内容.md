# 用js创建html页面中的标签内容

## 打开实验文件

单击右方的[js create html](https://codepen.io/quanbinn/pen/yLJvqPO), 浏览器里会打开一个新的页面，里面有下面的代码段，如下图所示。

```javascript
let createA = (url,text) => { 
	let a = document.createElement("a"); 	
	a.href = url; 
	a.innerHTML = text; 
	document.body.appendChild(a); 
} 
createA("https://gitee.com/quanbinn/Learn-Mathematical-Olympiad-The-Interactive-Way/blob/master/chapters/%E5%BE%AE%E5%88%86/%E5%88%B6%E4%BD%9C%E6%A2%AF%E5%BA%A6%E4%B8%8B%E9%99%8D%E5%AE%9E%E9%AA%8C%E7%9A%84%E5%AE%9E%E4%BD%93%E6%A8%A1%E5%9E%8B.md","单击教程链接，开始做实验"); 

let createInput = (type,value) => { 
	let input = document.createElement("input"); 
	input.type = type; 
	input.value = value; 
	document.body.appendChild(input); 
} 
createInput("button","购买学习道具"); 

//创建表格 
createTable = (w,h,r,c) => { 
	let table = document.createElement("table"); 
	let tbody = document.createElement("tbody"); 
	table.width = w; 
	table.height = h; 
	table.border = 1;    
	for(let i=1;i<=r;i++) { 
		let tr = document.createElement("tr"); 
		for(let j=1;j<=c;j++) { 
			let td = document.createElement("td"); 
			td.innerHTML = "序号："+ i + j; 
			//td.appendChild(document.createTextNode(i + "" + j)); 
			tr.appendChild(td); 
		} 
		tbody.appendChild(tr);    
	} 
	table.appendChild(tbody); 
	document.body.appendChild(table); 
} 
createTable(270,270,3,3); 
```

## Reference

1. [在js中使用createElement创建HTML对象和元素](https://www.cnblogs.com/azhqiang/p/4107738.html)



