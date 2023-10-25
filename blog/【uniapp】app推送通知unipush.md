打包需要开通push模块权限
```javascript
onLaunch: function() {
  // #ifdef APP-PLUS  
  const _handlePush = function(message) {  
    console.log(message);
    //跳转到某个指定的页面
    //uni.navigateTo({  
    //url: message.payload.pagePath  
    //});
  };
  //点击通知消息时执行的事件
  plus.push.addEventListener('click', _handlePush);  
  //收到透传消息时执行的事件
  plus.push.addEventListener('receive', _handlePush);  
  // #endif 
  console.log('App Launch')
}
```
