#react Router路由 实现单页面应用  
***  
 ###Router是react的一个组件   
 ####React Router   
 - 安装命令如下必须有环境   
 	npm install react-router-dom --save     
	
 ###使用需挂载  
 ```js
import React from 'react';
import Home from './home';
import About from './about';
import Work from './work';
import './style.css';
import {BrowserRouter as Router,Route, Link, Redirect,Switch,NavLink} from 'react-router-dom';
const NotFound = () => <h1>页面跑丢了</h1>
class App extends React.Component{
	render(){
		return(
			<Router>
				<div>
					<NavLink to='/' exact>首页</NavLink>
					<NavLink to='/about'>about</NavLink>
					<NavLink to='/work'>work</NavLink>
					<Switch>
						<Route exact path='/' component={Home}/>
						<Route path='/about' component={About}/>
						<Route path='/work' component={Work}/>
						<Redirect from='/old' to='/:work'/>
						<Route component={NotFound}/>
					</Switch>
				</div>
			</Router>
		)
	}
}
export default App;
//使用路由功能需要使用<Router>标签进行包裹是达到预期结果，<Route />  =>>  <Route exact path='/' component={Home}/> 主要是匹配线路找到对应的值，link和Navlink效果类似只是后者多了一个可以控制样式的class 默认类名为active 可以修改 用activeclassName
```