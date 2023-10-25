在react-router4.x以上，将router分为react-router-dom与react-router-native，开发web我们只需要安装react-router-dom就可以。其实它的一些传参、取参和原生的方法是非常类似的。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840935164-4662cedd-93bb-4b10-b8d7-b5d3ef325720.png#clientId=u88248e54-978a-4&from=paste&id=u879451f1&originHeight=451&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u74a6371d-c2cc-4b78-a6fc-bb03d00c2d6&title=)
## 一、params传参
params传参 刷新页面 数据存在；但是路由路径后面需要加上/:paramsName
我这里使用了react-router-config分离了路由配置
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840935860-2711f7f8-cb9a-4835-8e2f-3476cee08ec3.png#clientId=u88248e54-978a-4&from=paste&id=ueff29707&originHeight=232&originWidth=440&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ud7afd84f-fca7-4e4e-9874-7b075493dce&title=)
跳转：
```javascript
this.props.history.push("/my-order/123")
```
取参：
```javascript
this.props.match.params.id
```
## 二、state传参
state传参 刷新页面 数据会丢失
首先我们不传参直接this.props.history.push("/my-order")跳转打印下props：
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840936341-f8bfedf2-507b-4b50-bb39-7a578547ffd6.png#clientId=u88248e54-978a-4&from=paste&id=u33c8458e&originHeight=301&originWidth=610&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u4c54db38-8bec-45e1-80f7-a86827be217&title=)
以上并没有传任何参数，打印出来的都是原始数据，可以看出原始提供的参数并没有query，何谈query传参（网上各种没有实践就说query传参，刷新数据依然存在的不攻自破，当然了仅限于react-router-dom）
传参：
```javascript
this.props.history.push({
  pathname: "/my-order",
  state: {
    id: "123123"
  }
})
```
取参：
```javascript
this.props.location.state.id
```
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840937877-27c8694c-5dbd-46b8-9318-3f395110df27.png#clientId=u88248e54-978a-4&from=paste&id=ua003ee2d&originHeight=281&originWidth=560&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u14720a30-7b22-40d3-b60e-be06223f592&title=)
但是，实际测试我传参时，无论传什么字段的参数过来都能拿到，下来将state更换为任意的字段比如传参用rocyuan替换state
```javascript
this.props.history.push({
  pathname: "/my-order",
  rocyuan: {
    id: "123123"
  }
})
```
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840937374-c59d28b2-0ca8-4e7b-b761-854e00116d74.png#clientId=u88248e54-978a-4&from=paste&id=ud3f294df&originHeight=288&originWidth=608&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u261b1ee8-ee21-4f14-baaa-9211b71a845&title=)
取参也就自然变成this.props.location.rocyuan.id
那在将rocyuan更换为query呢？那肯定和最开始的state是一模一样的。。。再次验证网上误导人的说react-router-dom中的query传参。刷新页面数据依然是会成为undefined
## 三、search传参
search就是query传参；刷新页面数据依旧存在
传参（1）：
```javascript
this.props.history.push({
  pathname: "/my-order",
  search: "?id=123"
})
```
传参（2）：
```javascript
this.props.history.push("/my-order?id=" + 123)
```
取参：
```javascript
this.props.location.search
```
其实它取到的是search就是url后面的query，还需要处理：
```javascript
// 封装的取url的query方法，返回的对象就是转换query的对象
getUrlQuery(search) {
  const theRequest = new Object()
  if (search.indexOf("?") != -1) {
    const str = search.substr(1)
    const strs = str.split("&")
    for(let i = 0; i < strs.length; i ++) {
      theRequest[strs[i].split("=")[0]]=decodeURI(strs[i].split("=")[1])
    }
  }
  return theRequest;
}

// 使用
const  search = this.props.location.search;
const query = this.getUrlQuery(search);
```
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840938046-9c194927-b5d3-4dbf-a4ba-1efb4b91cdb0.png#clientId=u88248e54-978a-4&from=paste&id=ufed4c4aa&originHeight=306&originWidth=662&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uf4306e64-50bd-43d8-bb47-607920a5371&title=)
