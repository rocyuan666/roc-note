所有第三方授权登录及支付整体流程大概如下：
注册认证账号  —>  在此账号下申请创建应用  —>  再给该应用添加功能（授权登录、支付等功能。）
在给应用添加每一项功能时，每个功能的要求都有所不同（不同平台之间也有差异，需按照对应平台的要求缇提供）。比如支付需要有商户、提供上传营业执照等信息。

## 授权登录

uniapp登录鉴权功能需要到第三方开发平台申请应用后获取相关配置参数，并配置到uniapp打包配置中。
云端打包第三方授权登录只支持微信、QQ、新浪微博、apple（仅iOS13支持）。
参考地址：[https://ask.dcloud.net.cn/article/192](https://ask.dcloud.net.cn/article/192)

### 微信授权登录

微信授权登录需要：微信开放平台申请应用的AppID、AppSecret、Universal Links（ios平台通用链接）
微信登录，微信分享，微信支付配置的信息需要保持一致

- appid：微信开放平台申请应用的AppID值；
- appSecret：微信开放平台申请应用的AppSecret值；
- UniversalLinks：iOS平台通用链接，必须与微信开放平台配置的一致

微信开放平台地址：[https://open.weixin.qq.com/](https://open.weixin.qq.com/)
**注册认证微信开放平台需要的资料：**
![](assets/【记录】uniapp授权登录&支付/1.png)

### QQ授权登录

QQ授权登录需要：腾讯QQ开放平台申请应用的AppID
- appid：腾讯QQ开放平台申请应用的AppID值。

腾讯QQ开放平台地址：[https://connect.qq.com/](https://connect.qq.com/)
**注册认证QQ开放平台需要的资料：**
**公司接入：**

![](assets/【记录】uniapp授权登录&支付/2.png)

**个人接入：**

![](assets/【记录】uniapp授权登录&支付/3.png)

### 新浪微博授权登录

新浪微博授权登录需要：新浪微博平台应用appkey、appsecret、redirect_uri（授权回调页地址）

- appkey: "新浪微博平台应用appkey"；
- appsecret: "新浪微博平台应用appsecret"；
- redirect_uri: "新浪微博平台应用授权回调页地址"。

新浪微博开放平台地址：[https://open.weibo.com/](https://open.weibo.com/)

**注册认证微博开放平台需要的资料**

**公司接入：**

![](assets/【记录】uniapp授权登录&支付/4.png)

**个人接入：**

![](assets/【记录】uniapp授权登录&支付/5.png)

### apple授权登录

ios13+支持，App Store审核规范。

## 支付

在使用支付前，需要向各支付平台申请开通支付功能。
uniapp支付支持微信、支付宝、Apple应用内支付（ios）。
参考地址：[https://ask.dcloud.net.cn/article/71](https://ask.dcloud.net.cn/article/71)

### 微信支付

微信支付需要到微信开放平台开通支付功能，申请应用后可以获取AppID和AppSecret值。
微信登录，微信分享，微信支付配置的信息需要保持一致
开通支付功能后可获取支付业务服务器配置数据：

- **PARTNER**：财付通商户号
- **PARTNER_KEY**：财付通密钥
- **PAYSIGNKEY**：支付签名密钥

### 支付宝支付

支付宝支付需要登录支付宝开放平台，创建应用接入支付宝App支付能力。

- 创建应用（获取appid）
- 开通App支付功能
- 配置密钥（获取公钥、私钥）

支付宝开放平台地址：[https://open.alipay.com/platform/home.htm](https://open.alipay.com/platform/home.htm)

### Apple应用内支付

苹果应用内置流程
