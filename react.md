# react

- 声明式开发
- 与其他框架并存
- 组件化
- 单向数据流
- 视图层框架
- 函数式编程
- 轻量级视图层框架

### PropTypes

- propTypes 检验父组件传递过来的值的类型
- defaultProps 设置传递来的值的默认值

### props state 与render函数

- 当组件的state或者props发生改变，render函数会重新执行

- 父组件的render函数被执行时，子组件的render也会重新运行

### 虚拟DOM

- 虚拟dom是一个js对象，用它描述真实dom

- 生产新的虚拟dom（节约性能）

- 比较原始虚拟dom和新的虚拟dom的区别，找到区别，操作真实dom改变内容

- 比较虚拟dom（js对象）节约性能

- React减少了真实dom的创建和真实dom的对比，提升了性能

- react中的顺序：

  - state数据和jsx模版结合

  - 先生成虚拟dom
  - 用虚拟dom生成真实的dom

- jsx模版->createElement->js对象(虚拟dom)->真实dom
- 优点
  - 性能提升
  - 使跨端应用实现，react native

### 虚拟dom中的diff算法

- 如何比较虚拟dom（diff算法）
- setState异步，为了提升比对性能，间隔很短的几次会合并成一次setstate，再进行虚拟dom比对  
- 同层比对
- key值为了提高比对性能，不要用index作为key值，要选择稳定不会变的值作为key值

### ref使用

- Ref ={(input)=>{this.input=input}}
- ref获取dom
- 用来替换e.target
- 不推荐使用，尽量不要直接操作dom

### 生命周期函数

- 在某一个时刻，组件会自动调用执行的函数
- render是
- initialization
  - setup state and props
- Mounting 组件第一次放到页面上的时候
  - component will mount  组件即将被挂载到页面的时刻 只会执行一次
  - render
  - component did mount 组件已经被挂载到页面上之后 只会执行一次
- updation
  - props
    - component will receive props 当一个组件从父组件接受参数，只要父组件的render函数被重新执行，子组件的该函数就会被执行，如果子组件第一次存在父组件中，不会执行；如果已经在父组件中，会执行
    - should component update 避免不需要的更新，提升性能
    - Component will update
    - render
    - component did update
  - state
    - should component update
    - Component will update
    - render
    - component did update
- unmount
  - Componentwillunmount

### 发送ajax请求

- axios

  

### react-transition-group 实现动画效果

- csstransition
- Fade-enter
- Fade-enter-avtive
- Fade-enter-done
- fade-exit`, `fade-exit-active`, `fade-exit-done

### redux

- 数据层框架 
- reducer + flux
- Store 存储数据的公共区域 
- store 是唯一的
- store自己改变数据，而不是reducer
- reducer是个纯函数，有固定的输入，就会有固定的输出
- createStore
- store.dispatch(action)
- Store.getState
- Store.subscribe

### ui组件和容器组件

- ui组件负责渲染，容器组件负责处理页面逻辑
- 无状态组件，就是一个函数，性能更好

### redux-thunk

- 是redux的中间件, 创建store的时候引入
- action 返回函数
- 中间件：==action和store之间==，对dispatch升级，dispatch会先执行函数，store可以接受对象或者函数

### Redux-saga

### react-redux

- 第三方模块，帮助我们在react中更方便的使用redux                    