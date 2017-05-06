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
   
****

##key   ===  为react的dom节点设置一个唯一的参数便于底层运行是方便底层使用   


###ref关键字   


- ref是 React特殊的属性，你可以将这个属性加在任何通过render()返回的组件中。因为react中拿到的都是虚拟dom ,而ref可以拿到实例。  

```js
import React from 'react';
class App extends React.Component{
	handleClick(){
		this.input.focus()
		console.log(this.aaa)
	}
	render(){
		return (
			<div>
				<p ref={(test) => this.aaa = test}>talk i cheap,show me your code</p>
				<input placeholder='输入' ref={(input) => this.input =input}></input>
				<button onClick={this.handleClick.bind(this)}>点击</button>
			</div>
		)
	}
}
export default App;
```   
ref={(input) => this.input =input}  =>  第一个：形参   第二个：组件的属性   第三个：实参 拿到节点    
***

###filter方法js这是过滤方法 includes 方法




##props 组件与组件间的沟通

- 单项数据流：只能父级往子级传 组件App里有组件Btn,App为父组件

- 创建父组件的js中：Btn加一个属性A
- 创建子组件的js中：{this.prop.A}
- 变量为数字用{}，字符串`${}`
- 在创建子组件的js中：将父组件中所有定义过的属性全部写进去（this.props）,然后再写子组件本身默认的属性.defaultProps

- 安装好propTypes包，可以规定写入参数的数据类型   

```js
	Btn.propTypes={
		title:PropTypes.string,
		pad:PropTypes.number
	}
	children(特殊的props)
``` 
父组件：
```js

	<Card>
		<h1>fhdsjgh</h1>
		<h1>fhdsjgh</h1>
		<h1>fhdsjgh</h1>
		<h1>fhdsjgh</h1>
	</Card>
```
子组件：
{this.props.children} 写在标签的内部   
- 默认的props组件自带属性
```js
Tab.defaultProps ={
    index:0,
    title:'文章题目',
    date:'2017年4月30日'
}
```

   
###生命周期函数   
***

-  生命周期函数共三个阶段：初始化 更新 和 销毁      
1. 初始化阶段 4个过程      
	constructor(){}  组件创建时调用一次，返回值被保存下来     
	componentWillMount(){}  在组件渲染前只调用一次，     
	render(){} 渲染   
	componentDidMount(){} 初始化渲染后调用一次    
```js   
  import React from 'react';
import Btn from './btn';

class App extends React.Component{
	constructor(props){
		super(props);
		console.log('contructor')
		console.log(this.props)
		this.state = {
			num:0,
			name:this.props.name
			//{/*想要在这个位置用父级传给子集的props 可在上方强行呼叫props*/}
		}
	}
	componentWillMount(){
		console.log('will mount')//{/*渲染加载前 执行*/}
	}
	shouldComponentUpdate(){
		console.log('组件是否更新')
		return this.state.num <10 ? true : false
		//必须有返回值 而且必须是true 或 false
	}
	componentWillUpdate(nextProps, nextState){
		console.log('组件准备更新')
		console.log(nextProps, nextState)
		//传进的参数 更新之前触发
	}
	componentDidUpdate(prevProps, prevState){
		console.log('组件更新完毕')
		console.log(prevProps, prevState)
		//传进的参数 更新之后触发之前的值
	}
	render(){
		console.log(this.state.num)
		console.log('render')
		return(
			<div>
				{this.state.num}
				<button onClick={()=>this.setState({num:this.state.num+1})}>+1</button>
				<Btn num={this.state.num}/>
			</div>
		)
	}
	componentDidMount(){
	
	}
}
export default App;
//触发组件更新阶段的条件 props 或者 state 改变   
import React from 'react';
//import PropTypes from 'prop-types';

class Btn extends React.Component{
	constructor(){
		super()
		console.log('a')
		this.state={
			destroy:false//状态
		}
	}
	componentWillReceiveProps(nexProps){
		console.log('是否收到父级传输的Props属性')
	}
	componentWillUnmount(){
		console.log('将要消毁的组件')
	}
	render(){
		return(
			<div>
				<button onClick={()=>this.setState({destroy:true})}>删除</button>
				{this.state.destroy ? null : <div>test下的NUM:{this.props.num}</div>}
			</div>
		)
	}
}

export default Btn;
```
2. 更新   
 componentWillReceiveProps(){} 是否收到父级传输的Props属性   
 shouldComponentUpdate(){} 组件是否更新 必须有返回值 而且必须是true 或 false   
 componentWillUpdate(){} 传进参数后 更新之前触发  
 render()   
 componentDidUpdate(){} 组件同步到dom中立刻触发   
3. 销毁   
componentWillUnmount(){}  将要消毁的组件
    
 


	

