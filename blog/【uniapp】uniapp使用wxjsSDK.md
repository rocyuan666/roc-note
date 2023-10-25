wxjsSDK官方文档：[https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html#1](https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html#1)
公众号后台需设置“JS接口安全域名”！
# 安装jweixin-module
```bash
npm install jweixin-module
```
# 使用
以下例子为 h5微信支付
```javascript
const jweixin = require('jweixin-module');
const { payJssdkBuildConfig } = require('@/api/pay');




const config = await payJssdkBuildConfig();
/*
=== config 是后台返回的 data
{
    "code": 1,
    "msg": "",
    "time": "1670380349",
    "data": {
        "debug": false, // 开启调试模式,调用的所有 api 的返回值会在客户端 alert 出来，若要查看传入的参数，可以在 pc 端打开，参数信息会通过 log 打出，仅在 pc 端时才会打印。
        "appId": "微信公众号appid", // 必填，公众号的唯一标识
        "jsApiList": [
            "chooseWXPay"
        ], // 必填，需要使用的 JS 接口列表
        "nonceStr": "3AwvgHfj2n", // 必填，生成签名的随机串
        "timestamp": 1670380349, // 必填，生成签名的时间戳
        "signature": "3343130fecb59fb1114f90d975c34a79150c7f15" // 必填，签名
    }
}
*/
if(config) {
  jweixin.config(config);
  jweixin.ready(function () {
    /*
      data 是后台返回的支付所需信息
    */
    jweixin.chooseWXPay({
      timestamp: data.timeStamp, // 支付签名时间戳，注意微信jssdk中的所有使用timestamp字段均为小写。但最新版的支付后台生成签名使用的timeStamp字段名需大写其中的S字符
      nonceStr: data.nonce_str, // 支付签名随机串，不长于 32 位
      package: "prepay_id=" + data.prepay_id, // 统一支付接口返回的prepay_id参数值，提交格式如：prepay_id=\*\*\*）
      signType: "MD5", // 签名方式，默认为'SHA1'，使用新版支付需传入'MD5'
      paySign: data.paySign, // 支付签名
      success: function (res) {
        // 支付成功后的回调函数
      },
      fail: function (err) {
        uni.showToast({
          icon: "none",
          title: "支付失败"
        })
      },
    });
  });
  jweixin.error(function (res) {
    uni.showToast({
      icon: "none",
      title: "支付失败"
    })
  }); 
} else {
  uni.showToast({
    icon: "none",
    title: "支付失败"
  })
}
```

