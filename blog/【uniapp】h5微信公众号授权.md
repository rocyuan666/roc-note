微信公众号授权，前端调用微信提供的获取code地址携带好参数，参数中有回调地址（此地址域名必须与微信公众号后台配置网页域名一致）

成功后微信会将code携带在回调地址的query中（自行截取），再将code传给后台进行业务开发
非uniapp框架，逻辑基本一致

```javascript
onLoad(option) {
  // 判断缓存有无 openid
  if(uni.getStorageSync("openid")){
    this.openid = uni.getStorageSync("openid")
    // 有openid处理业务...
  } else {
    // 没有openid（进行授权获取code -> 获取openid -> 缓存openid -> 请求预约列表）
    this.getWxCode()
  }
},
methods: {
  // 请求openid
  getOpenId(code){
    const that = this
    uni.request({
      url: "获取openid的接口地址",
      method: "GET",
      data: {
        code: code
      },
      success(res){
        if(res.data.code == 200){
          that.openid = res.data.data
          uni.setStorageSync("openid", that.openid)
          // 有openid处理业务...
        }else{
          uni.showToast({
            mask: true,
            icon: "none",
            title: res.data.message
          })
        }
      }
    })
  },
  // 获取code
  getWxCode(){
    this.code = ""
    let local = window.location.href; // 微信授权重定向的 url
    const appid = this.appid
    this.code = this.getUrlCode().code
    // 如果没有code，则去微信服务器请求
    if (this.code == null || this.code === '') {
      window.location.href = `https://open.weixin.qq.com/connect/oauth2/authorize?appid=${appid}&redirect_uri=${encodeURIComponent(local)}&response_type=code&scope=snsapi_userinfo&state=STATE#wechat_redirect`
    } else {
      // 已经拿到code
      console.log(this.code, "code")
      this.getOpenId(this.code)
    }

    console.log(this.getUrlCode(), "code")
    console.log(local, "页面的local")
  },
  // 截取url中的code方法
  getUrlCode() {
    var url = location.search
    var theRequest = new Object()
    if (url.indexOf("?") != -1) {
      var str = url.substr(1)
      var strs = str.split("&")
      for(var i = 0; i < strs.length; i ++) {
        theRequest[strs[i].split("=")[0]]=(strs[i].split("=")[1])
      }
    }
    return theRequest
  },
}
```
