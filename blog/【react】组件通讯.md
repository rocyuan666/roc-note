组件通讯就是组件与组件之间的数据传递大致可分为：
父组件传子组件、子组件传父组件、非父子组件传递（兄弟组件传递等）
而react中父子组件的通讯核心是props，非父子组件通讯核心是context（暂时不谈redux）
## 父传子—props
其实这个props用法非常简单
将需要传给子组件的数据卸载组件标签的属性及属性值上，子组件的props对象中就会有传过来的值，那么这是什么原理呢？下面详解
```javascript
// 子组件
function Home(props) {
  return <h2>{props.num}</h2>
}
// 父组件
class APP extends React.Component {
  constructo(props) {
    super(props)
    // 可维护自己的state
    this.state = {
      message: "嗷~",
      num: 0
    }
  }
  render() {
    return (
      <h1>APP</h1>
      // 引入Home组件
      <Home num={num} />
    );
  }
}
```
## 子传父—props
一般子组件传数据给父组件，都是子组件触发某种事件然后将数据传出，vue中是应用了$emit，而react非常灵活，根本不需要那样
父组件传递给子组件一个回调函数，子组件调用回调函数时把数据传入回调函数的参数中就可以传递过来了。
```javascript
// 子组件
class Home extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
      num: 10
    }
  }
  handleClick() {
    this.props.getCCpnData(this.state.num)
  }
  render() {
    return (
      <div>
        <h2>Home</h2>
        <button onClick={e => this.handleClick()}>点击</button>
      </div>
    )
  }
}
// 父组件
class APP extends React.Component {
  getCCpnData(cData) {
    console.log(cData)
  }
  render() {
    return (
      <h1>APP</h1>
      // 引入Home组件
      <Home getCCpnData={this.getCCpnData} />
    );
  }
}
```
## 非父子组件—context（用法1）
非父子组件传值，vue中使用bus事件总线方式可以传递，理论上react这种方式也是可行的，但是react提供了context，它的用法简单分为：
1. 创建context
2. 发送数据（MyContext.Provider value={this.state.num}）
3.接收数据（函数组件接收与class组件接收方法不同，详情见下）
```javascript
/**
 * 跨组件传值（context）：
 * 1. 创建 context 组件
 */
const MyContext = React.createContext(10);

/**
 * 3. 类组件的接收法
 * About.contextType = MyContext;
 */
class About extends React.PureComponent {
  render() {
    console.log(this.context)
    return (
      <div>
        <h2>About</h2>
        <h3>我是App的孙组件，这是App传过来的值:{this.context}</h3>
      </div>
    )
  }
}
About.contextType = MyContext;

/**
 * 3. 函数组件的接收法
 * MyContext.Consumer
 */
// function About() {
// 	return (
// 		<div>
// 			<h2>About</h2>
// 			<MyContext.Consumer>
// 				{value => {
// 					return <h3>我是App的孙组件，这是App传过来的值:{value}</h3>
// 				}}
// 			</MyContext.Consumer>
// 		</div>
// 	)
// }

function Home() {
  return (
    <div>
      <h2>Home</h2>
      <About />
    </div>
  )
}

class App extends React.PureComponent {
  constructor(props) {
    super(props)
    this.state = {
      num: 12
    }
  }
  render() {
    return (
      <div>
        <h2>App</h2>
        {/* 
          2. 发送数据
          MyContext.Provider value={this.state.num}
          注意：Provider 的 value值没传就会使用 createContext(默认值)的默认值
        */}
        <MyContext.Provider value={this.state.num}>
          <Home />
        </MyContext.Provider>
      </div>
    )
  }
}


ReactDOM.render(
  <App />,
  document.getElementById("root")
)
```
## 非父子组件—context（用法2）
将createContext返回的对象解构出来，有两个组件Provider、Consumer
Provider用来传值、Consumer用来接收
**父组件：**
```javascript
export const {Provider, Consumer} = createContext("hello")

render里：
<Provider value={this.state.num}>
  <Header></Header>
</Provider>
```
**跨组件（假如是孙组件）：**
```javascript
import {Consumer} from "../../../index"

render里：
<Consumer>
{
  (value) => {
    return (
      <div>nav里跨组件拿到的num：{value}</div>
    )
  }
}
</Consumer>
```
