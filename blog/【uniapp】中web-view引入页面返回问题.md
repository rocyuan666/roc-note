uniapp中的web-view组件引入页面后，返回失效问题
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1629361005288-773b0356-41b9-4a94-abd6-b5eff6c74456.png#clientId=uc3f9fca7-edd7-4&from=paste&id=uf750697f&originHeight=246&originWidth=772&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u91594aba-a0a4-4cbc-9243-973dd6e834b&title=)
返回后发现报错：Uncaught ReferenceError: mui is not defined at
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1629361004829-c00e8d74-a4e1-48bc-82ba-4154608ec543.png#clientId=uc3f9fca7-edd7-4&from=paste&id=ucac8a418&originHeight=37&originWidth=529&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uc450ae8c-4230-41b4-a6d5-e1e80182515&title=)
有些网页使用MUI框架开发的，所以需要将 mui 的返回关闭
## 解决
```javascript
onReady() {
  this.clearMuiBack();
},
methods: {
  // 关闭mui返回
  clearMuiBack() {
    // #ifdef APP-PLUS
    var currentWebview = this.$scope.$getAppWebview().children()[0];
    //监听注入的js
    currentWebview.addEventListener("loaded", function() {
      currentWebview.evalJS("mui.init({keyEventBind: {backbutton: false }});");
    });
    // #endif
  },
}
```
