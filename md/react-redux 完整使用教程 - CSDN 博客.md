> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_41949144/article/details/107998907?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-1-107998907-blog-128078971.235%5Ev43%5Epc_blog_bottom_relevance_base9&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-1-107998907-blog-128078971.235%5Ev43%5Epc_blog_bottom_relevance_base9&utm_relevant_index=2)

[redux](https://so.csdn.net/so/search?q=redux&spm=1001.2101.3001.7020) 与 vuex 一样是一个组件的状态（数据）管理器，当我们需要在项目各组件中共享数据时可以使用。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2pwZy9uRFJoeTQ1eEJreEVtOUFEekdkRUM5U3M4T09rRGNLUWliVEtQUjYzRHJ4R3RhUWthcmJpY2RhUmhpYUVhSTI2Zm1IU1B6ZTVFbFRpYjN2UFp2OTk4QnpBdWcvNjQw?x-oss-process=image/format,png)

redux 是一个第三方的库，本身和 [react](https://so.csdn.net/so/search?q=react&spm=1001.2101.3001.7020) 没有任何关系，react-redux 也是一个第三方库，可以帮助我们在 react 项目中更好的使用 redux。

**_简介_**

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy9uRFJoeTQ1eEJreEVtOUFEekdkRUM5U3M4T09rRGNLUUNveE1XVDJiZ3pyZmplcnIxSTVjczhmVHQ3TWlhb1Bla2E5c013cVlSUXA2QnA3TlBLMGdqa1EvNjQw?x-oss-process=image/format,png)

redux 流程图

**store**（状态库）：用于存放组件中的 state。

**action**（动作）：redux 将每一次更改动作定义为一个 action，如

```
import actionTypes from './actionTypes'
 
const actionCreator = {
  getInputChangeAction: (val) => ({
    type: actionTypes.CHANGE_INPUT_VLAUE,
    value: val
  }),
  btnClickAction: (val) => ({
    type: actionTypes.BTN_CLICK,
    value: val
  }),
  listDelAction: (val) => ({
    type: actionTypes.LIST_DEL,
    index: val
  })
}
 
export default actionCreator;
```

**reducers**（执行）：是一个纯函数，将根据 action 的不同来修改 state。

**dispatch**（分发）：组件中通过 _dispatch(action)_，来实现动作的提交。

**1**

_**安装**_

```
const types = {
  CHANGE_INPUT_VLAUE: 'change_input_value',
  BTN_CLICK: 'btn_click',
  LIST_DEL: 'list_del'
}
 
export default types;
```

**2**

**用 react-redux 管理 todoList 数据**

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9uRFJoeTQ1eEJreEVtOUFEekdkRUM5U3M4T09rRGNLUWpiVlZYVUdabjZCcG1YRG1pYTlXdTl0SmVrU2lhaWNzQXUzemRYRDJUZU9ZT1FONUFMRUlvQ00zZy82NDA?x-oss-process=image/format,png)

**action（动作）分析：**

**输入框输入**

**按钮提交**

**列表点击删除**

**3**

**创建 action**

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X3BuZy9uRFJoeTQ1eEJreEVtOUFEekdkRUM5U3M4T09rRGNLUWR0UWliZm45MTJ0dlF1Q1NUVXppYWZkdWtpY1o3dTF4RGFKNjJMdFpRZkJjOVZLUTV4MWRiUndNdy82NDA?x-oss-process=image/format,png)

```
import actionTypes from './actionTypes';
 
const defaultState = {
  inputValue: '',
  list: [],
};
export default (state = defaultState, action) => {
  // reducer 可以接受state，但是绝不能修改state
  const newState = JSON.parse(JSON.stringify(state));
  switch (action.type) {
    case actionTypes.CHANGE_INPUT_VLAUE:
      newState.inputValue = action.value;
      break;
    case actionTypes.BTN_CLICK:
      newState.list.push(action.value);
      newState.inputValue = '';
      break;
    case actionTypes.LIST_DEL:
      newState.list.splice(action.index, 1);
      break;
    default:
      break;
  }
  return newState;
};
```

action 的 type 定义为常量放在 actionType.js 中统一管理，以避免 type 手写出错的可能。

actionTypes.js

```
import { createStore } from 'redux';
import reducer from './reducer';
 
const store = createStore(reducer);
 
export default store;
```

**4**

**定义 reducer**

reducer.js

```
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux'
import store from './store'
import TodoList from './components/TodoList';
 
// if (process.env.NODE_ENV === "development") {
// require('./mock/index.js');
// }
 
ReactDOM.render(
  <Provider store={store}>
    <TodoList />
  </Provider>,
  document.getElementById('root')
);
```

**5**

**创建 store**

index.js

```
const mapStateToProps = state => {
  return {
    value: state.inputValue,
    list: state.list,
  };
};
```

**6**

**利用 react-redux**

index.js

```
const mapDispatchToProps = dispatch => {
  return {
    inputChange: e => dispatch(actions.getInputChangeAction(e.target.value)),
    btnClick: value => dispatch(actions.btnClickAction(value)),
    listClick: index => dispatch(actions.listDelAction(index)),
  };
};
```

React-Redux 提供 **Provider** 组件，可以让容器组件拿到 state。上面代码中，Provider 在根组件外面包了一层，这样一来，TodoList 的所有子组件就默认都可以拿到 state 了。

**7**

**组件中创建 state、dispatch 的映射关系**

```
// ui组件
const TodoList = props => {
  const { value, list, inputChange, btnClick, listClick } = props;
  return (
    <div>
      <div>
        <input onChange={inputChange} value={value}></input>
        <button onClick={() => btnClick(value)}>提交</button>
      </div>
      <ul>
        {list.map((item, index) => {
          return (
            <li key={index} onClick={() => listClick(index)}>
              {item}
            </li>
          );
        })}
      </ul>
    </div>
  );
};
```

```
import React from 'react';
import { connect } from 'react-redux';
import actions from '../store/actionCreator';
 
const mapStateToProps = state => {
  return {
    value: state.inputValue,
    list: state.list,
  };
};
 
const mapDispatchToProps = dispatch => {
  return {
    inputChange: e => dispatch(actions.getInputChangeAction(e.target.value)),
    btnClick: value => dispatch(actions.btnClickAction(value)),
    listClick: index => dispatch(actions.listDelAction(index)),
  };
};
 
// todolist组件目前只有dom可以写成函数组件以提升效率；
// ui组件
const TodoList = props => {
  const { value, list, inputChange, btnClick, listClick } = props;
  return (
    <div>
      <div>
        <input onChange={inputChange} value={value}></input>
        <button onClick={() => btnClick(value)}>提交</button>
      </div>
      <ul>
        {list.map((item, index) => {
          return (
            <li key={index} onClick={() => listClick(index)}>
              {item}
            </li>
          );
        })}
      </ul>
    </div>
  );
};
 
// 容器组件
export default connect(mapStateToProps, mapDispatchToProps)(TodoList);
```

意思就是将 state 与 dispatch 都映射到 props，那么组件内就可以直接通过 props 来访问。

```
// ui组件
const TodoList = props => {
  const { value, list, inputChange, btnClick, listClick } = props;
  return (
    <div>
      <div>
        <input onChange={inputChange} value={value}></input>
        <button onClick={() => btnClick(value)}>提交</button>
      </div>
      <ul>
        {list.map((item, index) => {
          return (
            <li key={index} onClick={() => listClick(index)}>
              {item}
            </li>
          );
        })}
      </ul>
    </div>
  );
};
```

connect 连接组件

```
export default connect(mapStateToProps, mapDispatchToProps)(TodoList);
```

完整代码：TodoList.js

```
import React from 'react';
import { connect } from 'react-redux';
import actions from '../store/actionCreator';
 
const mapStateToProps = state => {
  return {
    value: state.inputValue,
    list: state.list,
  };
};
 
const mapDispatchToProps = dispatch => {
  return {
    inputChange: e => dispatch(actions.getInputChangeAction(e.target.value)),
    btnClick: value => dispatch(actions.btnClickAction(value)),
    listClick: index => dispatch(actions.listDelAction(index)),
  };
};
 
// todolist组件目前只有dom可以写成函数组件以提升效率；
// ui组件
const TodoList = props => {
  const { value, list, inputChange, btnClick, listClick } = props;
  return (
    <div>
      <div>
        <input onChange={inputChange} value={value}></input>
        <button onClick={() => btnClick(value)}>提交</button>
      </div>
      <ul>
        {list.map((item, index) => {
          return (
            <li key={index} onClick={() => listClick(index)}>
              {item}
            </li>
          );
        })}
      </ul>
    </div>
  );
};
 
// 容器组件
export default connect(mapStateToProps, mapDispatchToProps)(TodoList);
```

这样就实现了通过 react-redux 管理组件状态（数据）。

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9tbWJpei5xcGljLmNuL21tYml6X2dpZi9uRFJoeTQ1eEJreEVtOUFEekdkRUM5U3M4T09rRGNLUTFEN25KZFZFVmlhNmFrNFpKSVMycWdXb2lhU1F6TzhzbHNadW43b2NoZlMxbWliQlFNZVhwU0pTUS82NDA?x-oss-process=image/format,png)

![](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy8yNDI1MTczNC0yMjVmOGZmMzlmMDM4Nzc4LmpwZw?x-oss-process=image/format,png)

**全栈攻城狮进阶**

关注微信公众号，第一时间获取好文章！

_没有伞的孩子，只有努力奔跑。_