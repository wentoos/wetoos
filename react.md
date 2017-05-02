###构建Modules 模块主要有3种方法       
####第一种         

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
 这三个构建方法都用一个默认属性用来存储相应的值    
 ```js   
 
    constructor(x,y,father){
             super(father)
             this.x=x;
             this.y=y;
         }
         //super()
         //在子类中想要调用父类的方法就需要用到Super.将this指向父级
         //是调用父类的构造方法.
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

 - 在线图片不需要引模块  




 ###引入样式表     


-内部样式表  

```js   

    import  './style.css'  
        //以模块的方式引入样式 为内部样式表；     
```  

-行内样式表

```js      
class Hello extends React.Component {
 	render () {
    
	 	return (
	 		<div>
	 			<div style={{margin:'20px'}}>我是第三种</div>
	 		</div>
            
	 			)
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

```     
   对象的合并 合并到 目标对象中，  


   




