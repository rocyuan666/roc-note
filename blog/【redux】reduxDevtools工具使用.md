redux中的状态都是公共的，我们可通过reduxDevtools工具查看改变状态的每一步操作，及状态的变化情况。
reduxDevtools工具需要安装到浏览器扩展（google商店安装自备梯子），安装成功后console面板中会多出一个redux选项
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840505744-5391733e-316b-43cf-8742-d43963e5f206.png#clientId=u5b98e09c-12e6-4&from=paste&id=ud23d89b7&originHeight=242&originWidth=693&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u29cf6cdb-a9c4-4048-afd3-4be4eaf4c14&title=)
## 使用
参考：[https://github.com/yuanpeng666/redux-devtools-extension](https://github.com/yuanpeng666/redux-devtools-extension)
```javascript
const composeEnhancers = (typeof window !== 'undefined' && window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__) || compose;

composeEnhancers方法将中间件包裹起来
```
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840505570-190689ac-1433-438d-b7e0-b6aed9c91cac.png#clientId=u5b98e09c-12e6-4&from=paste&id=u992c3e95&originHeight=334&originWidth=968&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ua1180804-3734-4257-aec0-cc0a524967c&title=)
## 示例
每一步的action及state改变都可看到。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840505524-0c7959a2-b1dd-48ba-9859-a27d32ced79b.png#clientId=u5b98e09c-12e6-4&from=paste&id=u861c729a&originHeight=623&originWidth=706&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u56c965b4-f2eb-4393-8eca-5802290ca76&title=)
