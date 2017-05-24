# redux   
- redux 是为了简单的解决组件与组件间通话的问题, redux 在组件之间构建一个桥梁, 使交流变得简单.  
> [老师笔记] https://happypeter.github.io/js-tiger/redux-rev/1-hello.html  
[中文官网]  http://cn.redux.js.org/index.html
- redux 是个插件  
```
 npm i --save redux
```
> 因为 redux 不仅仅在 react 中使用所以这是一个通用的包, 需要另外一个插件来进行封装 react-redux    
```
npm i --save react-redux
```

### 制作 store 仓库   
- Redux 是数据流管理工具。使用 Redux 的最重要的一句话：

> 一切数据都要保存的 Store 之中，组件自己不保留自己的 state 数据   

- 再由组件自己去 store 中拿到想要的数据.

第一步 创建 store.js
- storejs 中就是存储axjx请求过来的数据, 不过现在使用假数据 (也叫状态树) 进行操作.

```
let comments = ['数据1','数据2']
```
- 如何修改 store 的状态树

> 这就用到 redux 提供的接口 createRedux 这个函数就行    

```
import { createStore } from 'redux'
```  

> 由 createStore 函数对 store 里数据进行封装之后就可以传出了
```
let store = createStore(storeData)
export default store
```

- 这样就将store 中的状态树全部导出了.

> screateStore( )  可接收三个参数, 其中必填的为 Reducer 修改器 preloadedState，预加载 State ，这一项是可选的
enhancer，增强器，选填  

###   reducer
reducer 和 store 一样是 redux 三大核心概念之一。reducer 是 一个函数，用来修改 store 中的数据。  
```
function commentReducer(state = [], action) {
  switch (action.type) {
    case 'ADD_COMMENT':
        return [...state, action.comment]
    default:
        return state
  }
}
```
>其中commentReducer(oldState , action)  => newState   
oldState: 代表原来的状态树   
action: 是从组件中接收的数据和数据类型，从而对数据进行分发，redux 同 react 有着一样的规定就是不能直接修改 store    
*可以通过对象的拷贝、数组的展开、数字等的间接修改来达到相应的效果   

### action
- 那么如何从组件发出 action 数据呢？
```
store.dispatch({type:'ADD_COMMENT',comment:comment})
```
- 而 store 负责接收 action 的正是 Reducer 经由这个函数间接的修改 store，
这样就达到我的目的了。
