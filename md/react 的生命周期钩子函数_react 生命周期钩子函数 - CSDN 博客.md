> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_43606158/article/details/89440850?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171575094416800226534964%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171575094416800226534964&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-89440850-null-null.142^v100^pc_search_result_base3&utm_term=react%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E9%92%A9%E5%AD%90&spm=1018.2226.3001.4187)

前言：
---

你有没有遇到过这样的问题:

*   组件的生命周期有哪些？为什么要有生命周期函数?
*   我应该什么时候去获取后台数据? 为什么很多教程都推荐用 componentDidMount? 用 componentWillMount 会有什么问题?
*   为什么 setState 写在这里造成了重复渲染多次？
*   setState 在这里写合适吗？

读完本文希望你能对 React 的组件[生命周期](https://so.csdn.net/so/search?q=%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F&spm=1001.2101.3001.7020)有一定的了解，编写 React 代码的时候能够更加得心应手，注意本文的生命周期讲的主要是浏览器端渲染，这是后端和全栈的主要使用方式，服务端渲染有些不一样，请注意区分，我们会在文中进行简单说明。  

#### 文章目录

*   [前言：](#_2)
*   *   *   [一、首先我们先来掌握基本单词](#_12)
        *   [二、全部生命周期总体分为三个执行阶段：](#_33)
        *   *   *   [1. 组件挂载](#1_34)
                *   [2. 组件更新](#2_86)
                *   [3. 组件销毁](#3_129)
                *   [5. 错误处理](#5_135)
        *   [三、react 生命周期执行的三个步骤【速查表】](#react_147)
        *   [四、强制刷新组件 -- forceUpdate](#__forceUpdate_149)

#### 一、首先我们先来掌握基本单词

掌握单词后会更好理解和记住生命周期：

<table><thead><tr><th>单词</th><th>意思</th></tr></thead><tbody><tr><td>constructor</td><td>构造函数</td></tr><tr><td>component</td><td>组件</td></tr><tr><td>will</td><td>将要</td></tr><tr><td>get</td><td>得到</td></tr><tr><td>default</td><td>默认值</td></tr><tr><td>initial</td><td>最初的</td></tr><tr><td>unsafe</td><td>不安全的</td></tr><tr><td>static</td><td>静态的</td></tr><tr><td>derived</td><td>衍生的</td></tr><tr><td>should</td><td>应该</td></tr><tr><td>update</td><td>更新</td></tr><tr><td>unmount</td><td>取消挂载</td></tr><tr><td>receive</td><td>收到</td></tr><tr><td>snap</td><td>提前</td></tr><tr><td>shot</td><td>拍摄</td></tr></tbody></table>

#### 二、全部生命周期总体分为三个执行阶段：

###### 1. 组件挂载

**(1)constructor**

可以理解为组件的第一个生命周期，一般会在这里初始化组件的内部状态 state 或者 进行方法绑定， 如果在这里面要使用 this 则必须在 super() 之后，如果在这里面需要使用 props，那么需要把 props 作为参数传入

```
constructor(props) {
  super(props);
  this.state = {
    color: '#fff',
    num: this.props.num,
  };
}
```

> 如果你不需要初始化状态也不需要绑定 handle 函数的 this，那么你可以不实现 constructor 函数，由默认实现代替。

**(2)static getDerivedStateFromProps**  
这个生命周期只要父组件重新渲染时就会触发。

设置了这个生命周期就不能设置 componentWillMount()  
这是 react16.3 之后新增的一个生命周期，这是一个静态方法。  
这个函数会在 render 函数被调用之前调用，包括第一次的初始化组件以及后续的更新过程中，每次接收新的 props 之后都会返回一个对象作为新的 state，返回 null 则说明不需要更新 state

> 静态方法没有 this 所以不能使用 setState。

(3)componentWillMount ------------ 17 版本即将废除

组件将要挂载，这个生命周期基本上没有什么用，而且 react*17 版本之后废弃。  
如果还想继续使用，可以使用 UNSAFE_componentWillMount 来代替，只不过不可与 static getDerivedStateFromProps 混用。

**(4)render**

react 最重要的步骤【React 组件的核心方法】，用于根据状态 state 和属性 props 创建虚拟 dom，进行 diff 算法，更新 dom 树都在此进行。此时就不能更改 state 了。  
这里是合成虚拟 DOM，可以理解为，在这里实际上都还没有真实的 dom。

> 我们应该保持该方法的纯洁性，这会让我们的组件更易于理解，只要 state 和 props 不变，每次调用 render 返回的结果应当相同，所以请不要在 render 方法中改变组件状态，也不要在在这个方法中和浏览器直接交互。

**(5)componentDidMount ------------- ajax 请求生成 DOM**

componentDidMount 方法会在 render 方法之后立即被调用，该方法在整个 [React 生命周期](https://so.csdn.net/so/search?q=React%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F&spm=1001.2101.3001.7020)中只会被调用一次。React 的组件树是一个树形结构，此时你可以认为这个组件以及他下面的所有子组件都已经渲染完了，所以在这个方法中你可以调用和真实 DOM 相关的操作了。

有些组件的启动工作是依赖 DOM 的，例如动画的启动，而 componentWillMount 的时候组件还没挂载完成，所以没法进行这些启动工作，这时候就可以把这些操作放在 componentDidMount 当中。

这个生命周期就是相当重要的一个生命周期，ajax 请求一般都在这里进行。

> 解决一个大家的疑问，为什么不在 componentWillMount 里面发请求：  
> 1. 要废除掉这个生命周期了  
> 2. 跟服务端渲染有关系（同构），如果在 componentWillMount 里获取数据，fetch data 会执行两次，一次在服务端一次在客户端，使用 componentDidMount 则没有这个问题。

###### 2. 组件更新

分为俩种情况，state 改变和 props 改变  
如果 state 改变，会直接进行到组件更新的第二个 shouldComponentUpdate, 如果是 props 改变，会先走 static getDerivedStateFromProps 或者 componentWillReceiveProps。

**(1)static getDerivedStateFromProps**  
**(1.1)componentWillReceiveProps ----- 17 版本即将废除**

16.4 之前，由于在更新阶段，没有 static getDeriveStateFromProps 这个生命周期，如果有根据 props 来生成的 state，就需要在这里重新设置一次。因为之前是在 constructor 里面根据 props 来初始化的 state，constructor 只会执行一次，所以要在 componentWillReceiveProps 来修正 state。在新的版本里，static getDerivedStateFromProps 这个生命周期不管是在装载还是更新的时候都会触发。因此，componentWillReceiveProps 也只会工作到 react17. 后续想要使用的话可以加前缀 UNSAFE_，但不可与 static getDerivedStateFromProps 一同使用。

**(2)shouldComponentUpdate 性能优化**

这个生命周期用于 react 的性能优化，接收俩个参数 (nextProps,nextState) 通常会根据这俩个参数和 this.state,this.props 来进行对比，根据比较的结果来 return true 或者 false, 如果 return 的是 false，将不会再执行后面的生命周期【也就是不会触发渲染】。

> 注意这个函数如果返回 false 并不会导致子组件也不更新。

> PS: 该函数通常是优化性能的紧急出口，是个大招，不要轻易用，如果要用可以参考 [Immutable 详解及 React 中实践](https://github.com/camsong/blog/issues/3) .

**(3)componentWillUpdate -----17 版本即将废除**

没什么卵用

**(4)render**

和 mount 阶段一样，生成虚拟 DOM

**(5)getSnapshotBeforeUpdate ----- 在最近一次渲染输出（提交到 DOM 节点）之前调用。**  
它使得组件能在发生更改之前从 DOM 中捕获一些信息（例如，滚动位置）。此生命周期的任何返回值将作为参数传递给 componentDidUpdate 的第三个参数。

> 此方法不常用，笔者就没在实战中使用过，官方文档说它可能出现在 UI 处理中，如需要以特殊方式处理滚动位置的聊天线程等。

**(6)componentDidUpdate**  
接收三个参数，分别是：preProps, preState, snapshot  
只有在组件使用了 getSnapshotBeforeUpdate 生命周期了才会用 getSnapshotBeforeUpdate 的返回值作为 componentDidUpdate 生命周期的第三个参数。否则第三个参数为 undefined

会在更新后立即被调用，首次渲染不会触发, 你可以在这个方法中进行 DOM 操作，或者做一些异步调用。  
一般用来根据判断 preProps 与 this.props 或者 preState 与 this.state 进行比较从而发请求或进行其他的一些处理。

###### 3. 组件销毁

**(1)componentWillUnmount**

组件将要销毁，这里一般可以用来清理定时器，解绑某些事件，取消网络请求等等。

###### 5. 错误处理

**（1）static getDerivedStateFromError ------ 会在子组件抛出错误后被调用**  
它将抛出的错误作为参数，并返回一个值更新 state。

> 注意事项：它会在渲染阶段调用，因此不允许出现副作用【比如请求等】，如遇此类情况，请改用 componentDidCatch

**（2）componentDidCatch ------ 同上**  
他接受俩个参数

1.  error 抛出的错误
2.  info 带有 componentStack key 的对象，其中包含有关组件引发错误的栈信息。

它会在 “组件提交” 阶段被调用，因此允许执行副作用。它应该用作于记录错误之类的情况。

#### 三、react 生命周期执行的三个步骤【速查表】

![](https://img-blog.csdnimg.cn/20201111100327786.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzYwNjE1OA==,size_16,color_FFFFFF,t_70#pic_center)

#### 四、强制刷新组件 – forceUpdate

默认情况下，当组件的 state 或 props 发生变化时，组件将重新渲染。如果 render() 方法依赖于其他数据，则可以调用 forceUpdate() 强制让组件重新渲染。

调用这个方法会跳过该组件的 shouldComponentUpdate()。