```javascript
/*
  微信授权
*/
(function () {
  var rocWxAuth = {
    openid: "",
    code: "",
    // appid: "wxe1518ed6c0a563a0",
    appid: "wxb44d9403cfa1339b",
    init: function () {
      this.wxAuth();
    },
    // 微信授权
    wxAuth() {
      var that = this;
      that.openid = localStorage.getItem("openid");
      if (that.openid) {
        console.log(that.openid, "有openid");
      } else {
        that.getWxCode();
      }
    },
    // 获取code
    getWxCode() {
      var that = this;
      var local = window.location.href; // 微信授权重定向的 url
      const appid = that.appid;
      that.code = that.getUrlCode().code;
      // 如果没有code，则去微信服务器请求
      if (that.code == null || that.code === "") {
        window.location.href = `https://open.weixin.qq.com/connect/oauth2/authorize?appid=${appid}&redirect_uri=${encodeURIComponent(
          local
        )}&response_type=code&scope=snsapi_userinfo&state=STATE#wechat_redirect`;
      } else {
        // 已经拿到code
        that.getOpenId(that.code);
      }
    },
    // 请求openid
    getOpenId(code) {
      var that = this;
      ROAjax.Post("/paving/Login/getOpenid", { code: code }, function (res) {
        if (res.code == 1) {
          that.openid = res.data.openid;
          localStorage.setItem("openid", that.openid);
        }
      });
    },
    // 截取url中的code方法
    getUrlCode() {
      var url = location.search;
      var theRequest = new Object();
      if (url.indexOf("?") != -1) {
        var str = url.substr(1);
        var strs = str.split("&");
        for (var i = 0; i < strs.length; i++) {
          theRequest[strs[i].split("=")[0]] = strs[i].split("=")[1];
        }
      }
      return theRequest;
    },
  };
  rocWxAuth.init();
})();

```
