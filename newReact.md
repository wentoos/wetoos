#### 从心出发  

#####  说在开头  
***  
- 上来就安装 git curl这两个插件 sudo apt-pet install git curl  
  git命令请看git.md

- 首先你得有node.js环境，没有了他你就是把枪落在家里的士兵，一般我们都使用nvm作为node版本管理工具 .   
   1.安装 nvm
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
执行上边的命令就可以安装 nvm 了。  
2.安装 node  
  - 查看有哪些版本可以安装
nvm ls-remote  
安装版本 v5.10.1  
nvm install v5.10.1  
这样就安装好了 node ，同时 npm 页就装好了。  
执行下面的命令来检查下本地的 node ，npm 版本吧。
```js
node -v
npm -v
```
如果是 windows 机器的话，直接到 node 官网下载对应版本的软件，双击安装即可。

- react 是一个大家族，拥有一个大家族，不仅仅是一个简单的 ×××.js，react主要有单页面应用React-router(路由)，还有在有时需要验证路由组件被正确使用，为此我们引入propTypes。React.PropTypes 提供很多验证器 (validator) 来验证传入数据的有效性。当向 props 传入无效数据时，JavaScript 控制台会抛出警告。注意为了性能考虑，只在开发环境验证 propTypes。，还有ajax请求(以axios为首的插件)，还有最主要的官方的环境包 create-react-app 。  
### 安装环境：  
1. 首先安装 create-react-app 命令 => npm install -g create-react-app   
这条命令会往我们的机器上安装一条叫 create-react-app 的命令，安装好以后就可以直接使用它来构建一个 react 的前端工程：create-react-app [项目名称]  
- 接下来就是启动项目了：
```
cd [项目名称]
npm start
```
*****
****
### 组件开发  
- 在react这里所有的dom都可以看成一个模块，最终网页就是一个个的模块组成的，
所有的组件都是由index.js进行渲染出去的，这是规定。  
```js
//index.js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './app';//将自己的创建的组件拿进来，必须有相对路径。
ReactDOM.render(<App />,document.getElementById('root'))//用reactdom组件将组件渲染到id为root下的dom中
```  
### 注意：  
1. 在react这里每个方法后不能跟标点，style行内样式要用 {{样式}} 进行包装，告诉组件这是一个整体    
***
###  创建组件 语法
- 创建组件有两种方法 ：  
1.class 命名法  
```js
class App extends React.Component {
    constructor() {
        super(),
        this.state={
            data:[]
        }
        render(){
            return(
                <div>我是第一个方法</div>
            )
        }
    }
}
export default App;
```
2.函数创建法
```JS

 function Hello(){
	return (
		<div>我是第二个方法</div>
	)
}
ReactDOM.render(<Hello /> , document.getElementById('root'))
```
- 这里要说的是组件要始终有返回值且只有一个jsx语句且每个html标签都得是闭合标签，jsx中所有地方都可以写 js 语句 只要用 {} 包裹起来就ok了。  
- 在jsx语法中有两个js的关键字class和表单for属性分别用 className 和 htmlFor 替换。   
****
### 组件的嵌套   
- 其实每个render组件都可以像html一样嵌套使用，并且可以重复使用  
```js
class Father extends React.Component{
    constructor(){
        super(),
        this.state={
        }
    }
    render(){
        return(
            <div>
                我是父组件
                <Child />
            </div>
        )
    }
}
class Child extends React.Component{
    constructor(){
        super(),
        this.state={
        }
    }
    render(){
        return(
            <div>
                我是子组件
            </div>
        )
    }
}
```
****
### 事件监听 => 就是添加onClick onChange onKeyDown 等来实现事件的绑定  
- 注意事件绑定后this始终指向组件的本身，如需要将this绑定到元素本身需要 .bind(this)
```js
class Title extends Component {
  handleClickOnTitle (e) {
    console.log(this)
  }
  render () {
    return (
      <h1 onClick={this.handleClickOnTitle.bind(this)}></h1>
    )
  }
}
```    
### state 和 setState
- state 是储存数据状态和配置参数容器，而setState则是修改state的方法   
```js
constructor(){
    super(),
    this.state={
        data:[]
    }
}

setTextState(){
    this.setState({data:[...this.state.data,newData]})
}
```
- 当你设置修改 state 时，他与setState通常都是异步的。   
***
### props 组件间的通讯    
- 通过父组件给子组件传递 props 来实现需要的功能  
```js
class Index extends Component {
  render () {
    return (
      <div>
        <LikeButton likedText='已赞' unlikedText='赞' />
      </div>
    )
  }
}
/////////// 子
class LikeButton extends Component {
  constructor () {
    super()
    this.state = { isLiked: false }
  }

  handleClickOnLikeButton () {
    this.setState({
      isLiked: !this.state.isLiked
    })
  }

  render () {
    const likedText = this.props.likedText || '取消'
    const unlikedText = this.props.unlikedText || '点赞'
    return (
      <button onClick={this.handleClickOnLikeButton.bind(this)}>
        {this.state.isLiked ? likedText : unlikedText}
      </button>
    )
  }
}
```
- props 还可以传对象、函数等   
- 默认配置 defaultProps
 - 上面的组件默认配置我们是通过 || 操作符来实现。这种需要默认配置的情况在 React.js 中非常常见，所以 React.js 也提供了一种方式 defaultProps，可以方便的做到默认配置。
 ```js
 class LikeButton extends Component {
  static defaultProps = {
    likedText: '取消',
    unlikedText: '点赞'
  }

  constructor () {
    super()
    this.state = { isLiked: false }
  }

  handleClickOnLikeButton () {
    this.setState({
      isLiked: !this.state.isLiked
    })
  }

  render () {
    return (
      <button onClick={this.handleClickOnLikeButton.bind(this)}>
        {this.state.isLiked
          ? this.props.likedText
          : this.props.unlikedText}
      </button>
    )
  }
}
```
- 传进来的 props 是无法修改的   
***
### 渲染数据   
- 一般渲染数据有二种：  
 1.直接将数据存放在数组当中，然后将数组里的数据利用 for 循环 push 到jsx中，就可完成渲染。  
 2.利用 .map 函数渲染  
 ```js
data.map(
    (item,index,arr)=>
        <div key={index}>{item.title}</div>
)
 ```
 - 在 react 中，生成的元素都要有 key 一个唯一的值，解决元素复用问题。  
****
### 状态提升   
- 当俩个组件使用同一个数据是交由他们同一个父组件统一管理，这个状态交状态提升
`
`
`
`
`
`
`
`
`
`
`
`
`
`
`
`
`
`
