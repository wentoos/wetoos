#react 组件   


   
 ##ES6

先要知道 ECMAScript就是JavaScript中的语法规范！ 它定义了很多重要的东西，包括：

* 语法 – 解析规则，关键字，语句，声明，操作等

* 类型 – 布尔型，数字，字符串，对象等

原型和继承

* 内置对象和函数的标准库 – JSON，数字（Math），数组方法，对象内省的方法等等。

- JavaScript由三部分组成：

  1. ECMAScript（核心）
  2. DOM（文档对象模型）
  3. BOM （浏览器对象模型）
  4. ECMAScript标准的版本分别是1、2、3、5、6、7。

Es6新增了许多特性。
   
    
##1. Let + Const 块级作用域和常量
 *** 
 ###let
    let 有严格的作用域，并没有所谓的声明提升，严格遵守作用域规则，只会存在于{ }之中，但定义全局变量时，this指向window。
***
	
--主要有3种方法       
####第一种         
** 
```JS
	React.createClass({
	render: function () {
		return (
			<div>我是第一个方法，即将消失</div>
		)
	}
})
ReactDOM.render(<Hello_></Hello_> , document.getElementById('root'))
//使用时假装是个标签来用<Hello_><Hello_ />
```
-**必须有render方法         


####第二种      

```JS
function Hello(){
	
		return (
			<div>我是第二个方法
			<Hi></Hi>
			</div>
		)

}
ReactDOM.render(<Hello /> , document.getElementById('root'))
```

####第三种方法 class       


```js

 class Hello extends React.Component {
 	render () {
	 	return (
	 		<div>我是第三种</div>
	 	)
 	}
 }
 ReactDOM.render(<Hello /> , document.getElementById('root'))
 ```



 ###引入图片模块          


 ```js
 import img from './footer.jpg';

 class Hello extends React.Component {
 	render () {
	 	return (
	 		<div>
	 			<div>我是第三种</div>
	 			<img src={ img } />
	 			<img src="https://timgsa.baidu.com/timg?image&qual51016135551745.jpg" />
	 		</div>
	 			)
 	}
 }
 ReactDOM.render(<Hello /> , document.getElementById('root'))
 ```

 -**在线图片不需要引模块  




 ###引入样式表     


-内部样式表
```js
import  './style.css'  //以模块的方式引入样式 为内部样式表；     
```  

-行内样式表

```js

class Hello extends React.Component {
 	render () {
	 	return (
	 		<div>
	 			<div >我是第三种</div>
	 			<img alt="666" />
	 		</div>
	 			)
 	}
 }
 //style 属性使用驼峰命名法书写，伪类样式不支持；
 ```




### theme 风格

```js   
import React from 'react';
export let blueStyle = 'blue'
```
类似于引入插件 修改对应的js就可修改所有主色调；



###对象合并  es7新增   


```js
let c ={a:1};
let s ={b:2};
let e ={c:3};
Object.assign(c,s,e);
console.log(c);
//对象的合并 合并到 目标对象中，
```
类似于


