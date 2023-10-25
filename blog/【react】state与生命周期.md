## state
state是组件自己私有的数据，函数组件要拥有自己的私有state需要改成class组件（暂时不说hooks）。
```javascript
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
    return <h1>APP</h1>;
  }
}
```
## 修改state—setState
要修改组件state必须使用react对象中Component提供的setState()方法,不能直接修改state，这样视图不会更新。
```javascript
class APP extends React.Component {
  constructo(props) {
    super(props)
    // 可维护自己的state
    this.state = {
      message: "嗷~",
      num: 0
    }
  }
  changeNum(i) {
    this.setState({
      num: this.state.num + i
    })
  }
  render() {
    return (
      <h1>this.state.num</h1>
      <button onClick={e => this.changeNum(1)}>+1</button>
    );
  }
}
```
以上可以看到我们使用this.setState()方法，但是我们App类并未实现setState方法，原因是我们App类继承了React.Component类，而react的Component类原型有setState方法。setState方法传参后面详细分析。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628839124359-ea7d9745-0003-4f46-bcf0-69f1ebb80db2.png#clientId=ud0795d28-d8e6-4&from=paste&id=u05e3caae&originHeight=318&originWidth=499&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u6cdb8e2e-799b-4ab8-b6d0-9f630f29ef6&title=)
## 组件生命周期
组件生命周期则是组件从创建到销毁的过程
```javascript
class APP extends React.Component {
  render() {
    return (
      <h1>App</h1>
    );
  }
  // 组件渲染dom
  componentDidMount() {
  }
  // 组件卸载
  componentWillUnmount() {
  }
  // ......
}
```
