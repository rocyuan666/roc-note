uniapp开发app检查版本更新，可在每次打开app检查更新（也就是App的onLaunch生命周期里）进行检查更新。
若有更新：模态框提示用户“是否选择更新”；选择是则选择浏览器，打开更新下载app的url，进行下载更新。
示例代码：
```javascript
onLaunch: function() {
  console.log('App Launch')
  // #ifdef APP-PLUS
  // 真机运行不需要检查更新，真机运行时appid固定为'HBuilder'
  if (plus.runtime.appid !== 'HBuilder') {
    uni.request({
      url: '检查更新的服务器地址',
      data: {
        appid: plus.runtime.appid,
        version: plus.runtime.version,
        imei: plus.device.imei
      },
      success: (res) => {
        // 根据实际返回结果处理判断
        if (res.statusCode == 200 && res.data.isUpdate) {
          // 提醒用户更新
          uni.showModal({
            title: '更新提示',
            content: res.data.note ? res.data.note : '是否选择更新',
            success: (ee) => {
              if (ee.confirm) {
                plus.runtime.openURL(res.data.url);
              }
            }
          })
        }
      }
    })
  }
  // #endif
},
```
