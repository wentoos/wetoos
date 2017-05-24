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
createStore()  可接收三个参数, 其中必填的为 Reducer
