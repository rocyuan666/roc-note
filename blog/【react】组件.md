组件允许你将 UI 拆分为独立可复用的代码片段，并对每个片段进行独立构思。——react官网
react中组件分为**函数组件**与**class（类）组件**
## 函数组件
函数组件就是编写js函数，下面这个js函数就是一个“函数组件”。
```javascript
function App() {
  return <h1>App</h1>;
}
```
## 类组件
类组件就是使用ES6中的class编写，下面这种class组件写法与上面函数组件写法是等价的，但是他两也是有区别的。
```javascript
class APP extends React.Component {
  render() {
    return <h1>APP</h1>;
  }
}
```
组件名我们会使用大写字母开头；因为React 会将以小写字母开头的组件视为原生 DOM 标签。
## 函数组件与class组件区别
函数组件无法维护自己的数据状态（state）以及生命周期，而class组件可以，这是它俩最大的区别（除非使用react hooks，先不说hooks）。
```javascript
// 函数组件（无法维护自己的state与生命周期）
function App(props) {
  return <h1>App</h1>;
}

// class组件
class APP extends React.Component {
  constructo(props) {
    super(props)
    // 可维护自己的state
    this.state = {
      message: "嗷~"
    }
  }
  // 自己的生命周期（只写一个举栗子）
  componentDidMount() {
    console.log("组件已经被渲染到 DOM")
  }
  render() {
    return <h1>APP</h1>;
  }
}
```
