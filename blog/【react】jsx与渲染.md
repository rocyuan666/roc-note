## jsx是什么？
jsx对js进行了语法扩展，可让我们在js中嵌入任何html标签，可以把html标签存入变量等操作，它是拥有js的全部功能；
但是我们以script标签引入react的方式使用jsx是需要Babel进行转化的，不然script是不会识别jsx；
jsx根元素只能有一个元素或组件，若需要换行必须用()包裹。
jsx示例如下：
```javascript
const el = (
  <h1 className="react">
    Hello, React!
  </h1>
);
```
## jsx中嵌入表达式
```javascript
const name = "RocYuan";
const el = <p>{name}</p>
```
## jsx中添加class属性等
```javascript
// jsx中为了区分css属性的class与es6的class，属性的class则用className，label标签中的for则用htmlFor替换
const el = <p className="name">{name}</p>
<label htmlFor="inputName"></label>

// 所有添加的属性如果为动态都可用{}嵌入
const name = "RocYuan";
const titleMessage = "RocYuanMessage"
const el = <p title={titleMessage } className="name">{name}</p>

// 添加img的url
const element = <img src={user.avatarUrl} />;

...其他属性嵌入皆可用{}
```
## jsx中绑定事件
```javascript
<button onClick={e => console.log(点击了按钮)}>按钮</button>
```
## jsx条件渲染
React 中的条件渲染和 JavaScript 中的一样，使用 JavaScript 运算符 if 或者条件运算符来创建元素来表现当前的状态，然后让 React 根据它们来更新 UI。完全可以模拟vue中的v-if 、v-show…
```javascript
function UserGreeting(props) {
  return <h1>Welcome back!</h1>;
}

function GuestGreeting(props) {
  return <h1>Please sign up.</h1>;
}

function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
}

ReactDOM.render(
  // Try changing to isLoggedIn={true}:
  <Greeting isLoggedIn={false} />,
  document.getElementById('root')
);
```
## jsx中列表渲染及key
渲染列表我门可以使用map方法
```javascript
class App extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
      movies: ["哪吒", "西游记", "三国演义"]
    }
  }
  render() {
    return (
      <div>
        {
          this.state.movies.map((item, index) => {
            // 这里key暂时用index，但这样是不对的，开发时应用唯一标识id之类（作用就不用多说了）
            return <p key={index}>{item}</p>
          })
        }
      </div>
    )
  }
}
```
## jsx中表单元素
React 中，可变状态（mutable state）通常保存在组件的 state 属性中，并且只能通过使用this.setState()来更新。
[https://react.docschina.org/docs/forms.html](https://react.docschina.org/docs/forms.html)
## 渲染
元素渲染使用react-dom中的render函数渲染。
它需要三个参数：
1. 渲染的组件
2. 需要插入的DOM节点
3. 渲染后的回调（但是一般用不到，所以可不传）
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628838250486-b3660b5c-3612-45e7-acb8-9adebd453416.png#clientId=u8890d826-66e4-4&from=paste&id=u24363fc9&originHeight=123&originWidth=447&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uce9ede0a-133f-4135-8e4e-4ad75c922f6&title=)
```javascript
function App() {
  return(
    <div>
      <h2>App</h2>
    </div>
  )
}
ReactDOM.render(
  <App>,
  document.getElementById("root");
)
```
## jsx的本质
实际上，jsx是FB为我们提供的一种语法糖，Babel 会把 JSX 转译成React对象中的createElement方法（当然我们也可以直接调用它，不使用jsx），vue3中的Vue.h()方法也是借鉴这的。
可通过babel网站工具看到jsx用js的实现的写法：[https://www.babeljs.cn/repl](https://www.babeljs.cn/repl)
```javascript
const el = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628838250501-4b345b39-6963-4de7-90d3-4ae91a37bf63.png#clientId=u8890d826-66e4-4&from=paste&id=u9fbc5144&originHeight=214&originWidth=507&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u9b189b21-52fb-4e26-bef0-d32a40ff36a&title=)
