uniapp中app转跳打开微信小程序需要使用`plus.share`模块，打包时必须勾选share模块，选择微信分享填入appid（此处的appid是微信开放平台申请应用的appid）。
**注意：没有认证的开放平台账号，只能跳转同主体下的小程序**
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1617938553650-0e52863a-5220-408d-b720-6b65bfe4ff5d.png#from=url&id=XfbQ4&originHeight=326&originWidth=595&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628841342218-a0ceccf5-e607-4086-86af-de2dd04d72dc.png#clientId=u8aa70001-f724-4&from=paste&id=uf6ae284c&originHeight=400&originWidth=848&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u842a7747-cb2f-4740-a19e-45c60a53407&title=)
需要使用plus.share.getServices，获取微信分享服务对象，再使用launchMiniProgram调用微信小程序。
示例代码：
```vue
towxapp() {
  // #ifdef APP-PLUS
  plus.share.getServices(function(res) {
    var sweixin = null;
    for (var i = 0; i < res.length; i++) {
      var t = res[i];
      if (t.id == 'weixin') {
        sweixin = t;
      }
    }
    if (sweixin) {
      sweixin.launchMiniProgram({
        id: 'gh_24624714f0f9',  // 小程序原始id
        type: 0,  // 0-正式版； 1-测试版； 2-体验版。 默认值为0
      });
    } else {
      plus.nativeUI.alert('当前环境不支持微信操作!');
    }
  }, function(res) {
    console.log(JSON.stringify(res));
  });
  // #endif
},
```
launchMiniProgram的属性值：

- id: (String 类型 )微信小程序ID；注意：是微信小程序的原始ID（”g_”开头的字符串）。
- path: (String 类型 )微信小程序打开的页面路径
- type: (Number 类型 )微信小程序版本类型；可取值： 0-正式版； 1-测试版； 2-体验版。 默认值为0。
- webUrl: (String 类型 )兼容低版本的网页链接

示例：
![](https://cdn.nlark.com/yuque/0/2021/gif/2779910/1628841342219-35c4d587-613d-4189-bf52-e910a5bfe7dd.gif#clientId=u8aa70001-f724-4&from=paste&id=u79f2e2b0&originHeight=696&originWidth=357&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uc9d0c616-f9be-4fc4-a46c-7dc66bf2649&title=)
