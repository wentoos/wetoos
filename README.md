#变量的解构赋值
##use strict严格模式
##const用const声明的变量，只能读不能更改。

```js
const b = 6; b=8;
```
##let数组里的值，可以是数字、变量、对象、函数等、空格占位但无法拿到。

```js
Let  [a,b,c,d,,] = [1,"aaa",{name:'sayname'},function(){}];
console.log(a,b,c,d);
```

##对象的结构赋值：将obj中的对象foo赋值给一个变量。

```js
let obj = {bar:'bbb',foo:'aaa',name:'sayname'};
let {foo} = obj;
console.log(foo);
var foo = obj.foo;

```

##字符串的结构赋值：按字符串下标赋值。

```js
const [a,b,c,d,e] ='hello';
console.log(a,b,c,d,e);
```

##对象的结构赋值：	

```js
let name = 'liuenqing';
let age = 22;
let say = function(){
	console.log(1)
}
let obj = {
	name,
	age,
	say,
	run(){
		console.log('run')
	}
}
console.log(obj)
```
##箭头函数：()为参数一个的时候可以省略、多个不能省略用,隔开、没有的时候不能省略。
 =>为返回值，返回一个对象的时候用小括号包起来。
执行多条js语句用{}包起来,需要自己写返回值。
箭头函数指向的this在声明时就会绑定，以后所有的this都指向声明时的this。
```js
let a = () => 8;等于
function a() {
	  return 8;
	}
```js
let a = (num,num1) => num*num1;
console.log(a(5,8));
```
```js
let a = (num,num1) =>{
	num++;
	num1++;
	return num+num1;
}
console.log(a(5,8));
```
```js
let a = (num,num1) =>({name:'sayname'});
console.log(a)
```
```js
function foo(){
	console.log(this);
	setTimeout(() =>{
		console.log(this);
		console.log(this.id);
	},1000)
};
var id = 21;
foo.call({id:42},12);
```
#字符串模版：
将字符串用``包起来，变量用${}包起来,
${}里可以写对象，进行进一步的运算等;
```js
var name = '刘恩庆';
var age = 24;
var str = `<p class='active'>姓:${name.charAt(0)}<br/>名:${name.substr(name.length-2,2)}<br/>年龄:${age}</p>`
document.body.innerHTML = str
```
#函数定义默认值：
()括号内为{参数时}拿对象的参数
```js
function sum(num = 5){
	return ++num
}
console.log(sum())
```
```js
function sum({name}){
	console.log(name)
}
sum({name:'liuenqing',age:'24'});
```
##...rest是定义函数的时候做为多个参数传入,关键字是(...)
```js
function arr(a,...rest){
	console.log(a)
	console.log(rest)
}
arr(1,2,3,4)
```
##arr.reduce(pre,cur,curIndex,array)
previousValu上一次值
currentValue 当前值
currentIndex 当前值的索引
array 数组
.reduce()是数组的方法,
```js
let a = [0,1,2,3,4].reduce(function(acc,cur,curIndex,arr){
	console.log(acc,cur,curIndex,arr);
	return cur
})
console.log(a)
```
```js
//用reduce()求最大值
let max = [0,1,10,2,3,4,6].reduce(function(acc,cur){
	return acc>cur?acc:cur
})
console.log(max)
```
##spread扩展操作符
```js
var arr = [1,2,3,4,5]
var arr1 = [6,7,8]
var arr2 = [...arr,...arr1,9]
console.log(arr2)
console.log(...arr2)
```
##modules模块
```js
//命名导出
let str = "liu";
let obj = {age:'55'};
export{str,obj};
//默认导出 export default str;
//导入
import {str as ccc,obj} form './test.js';
//导入的对象放在大括号里,as:将str做为ccc使用,找不到str,注意空格,
多次重复执行同一句import语句，那么只会执行一次，而不会执行多次
console.log(str);
```
##数组的map:实现for循环的功能,可以随意在map里面写函数
```js
var arr = ['val1', 'val2', 'val3'];  
for(var i = 0; i < arr.length; i++){ 
console.log(arr[i]); 
console.log(i); 
console.log(arr); 
} 
arr.map(function(val, index, array) { 
console.log(val); 
console.log(index); 
console.log(array); 
}); 
```
##数组循环变量forEach()
```js
let arr = [1,2,3,4,5];
arr.forEach(item => {console.log(item)})
//等于 for(var i=0;i<arr.length;i++){
//		console.log(arr[i]);
//}
```
##数组循环变量 keys()返回一个所有元素为字符串的数组.
```js
var arr = ["a", "b", "c"];
alert(Object.keys(arr)); 
// 弹出"0,1,2"
/* 类数组对象 */ 
var obj = { 0 : "a", 1 : "b", 2 : "c"};
alert(Object.keys(obj)); 
// 弹出"0,1,2"var arr = ["a", "b", "c"];
```
class的基本语法,用extends继承类,私有属性也会被继承
```js
//class关键字:定义一个类
//constructor构造方法:私有属性,一直存在没有为空
//this关键字:代表实例对象
//toString定义一个类:
class Point{
  constructor(x,y){
    this.x = x;
    this.y = y;
  }
  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }
}
var p = new Point(1,2);
console.log(p);
```
extends关键字:实现继承
```js
class Point{
  //constructor(father){this.father = father}
  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }
}
//定义一个类Point2,继承了Point类的所有属性 方法
class Point2 extends Point {
	constructor(x,y,father){
		//调用父类的constructor.father
		//子类只有用super才能添加私有属性
		super(father);
		this.x = x;
		this.y = y;
		console.log(123)
	}
	say(){
		console.log('Point2 say');
	}
}
var p =new Point2(5,8,888);
console.log(p);
```
注意!!!
class [name] {} 定义类;
class [name] extends [fathername]{}继承类
class内只能写方法,方法之间不加逗号;
class名字首字母大写;
class内的方法内一切正常;
super子类添加私有属性加super;
```js
class Father{
	_render(){
		throw new Error('子类必须实现')
	}
	render(){
		return(`
			<ul>
				${this._render()}
			</ul>
			`)
	}
}
class Son extends Father{
	_render(){
		return(`
			<li>aaa</li>
			`)
	}
}
var son = new Son();
console.log(son.render());
document.body.innerHTML = son.render();
```
##jsx 语法

1.jsx 语法需要bebel进行编译，转变为React.Element();

2.Adjacent JSX elements must be wrapped in an enclosing tag (4:30)
相邻的jsx语法，必须包裹在一个盒子里；

3.每个标签必须闭合， Unterminated JSX contents，单标签是使用自关闭标签方式书写，例如<input value ="aaa"  /> <br/>

4.当标签中有class属性时 需要使用className 替换，for 用 htmlFor；

5.标签严格区分大小写，

6.jsx语法中可以嵌入变量和值职表达式，可以写js语法，不可以写js语句；=>>>用{}包裹，


###react 组件   

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
	 			<img src={ img } alt="666" />
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



###对象合并  es7    


```js
let c ={a:1};
let s ={b:2};
let e ={c:3};
Object.assign(c,s,e);
console.log(c);
//对象的合并 合并到 目标对象中，
```


   

