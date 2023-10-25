react-redux可以不用我们手动的联系react与redux，它提供的：
Provider组件：需要告知它我们创建的store
connect方法：它接收两个参数，这俩参数分别是函数，函数参数返回一个对象，而connect方法返回的是高阶组件可传入一个组件返回一个增强后的组件。
– mapStateToProps：它提供一个参数 state，就是我们发生变化的store中的state
– mapDispatchToProps：它也提供一个参数dispatch，就是我们store的dispatch
而它们返回的对象都会放到组件的props中。
## 示例
拿到react-redux中的Provider组件传入我们创建的store
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840266139-689a28fc-8dfa-4bac-bc42-cae16598fcd0.png#clientId=ua3cfc93d-b075-4&from=paste&id=u44415da3&originHeight=567&originWidth=786&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ua7a220cf-f45c-44e6-a68d-5cf23ec3ca3&title=)
使用connect方法将定义的mapStateToProps，mapDispatchToProps传入并且将App组件传入它返回的高阶组件，将参数中的对象放入App组件的props中
所以我们才可以在App组件的props中拿到num数据与handleAddNum方法。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840265192-7ce7c1f8-729f-4e8c-ba54-b0194bd712d6.png#clientId=ua3cfc93d-b075-4&from=paste&id=u1a316449&originHeight=533&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ued594ec2-c373-4838-8960-19abac07542&title=)
## 示例结果
![](https://cdn.nlark.com/yuque/0/2021/gif/2779910/1628840267601-19fb15c5-42fe-4c41-bafe-ac65a945e44f.gif#clientId=ua3cfc93d-b075-4&from=paste&id=u50eae755&originHeight=138&originWidth=128&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uf05001c2-91d8-4333-9e22-ee1c13679e9&title=)
