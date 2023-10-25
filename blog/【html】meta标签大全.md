个人工作常用（TX互娱cp）：
## PC：
```html
<meta charset="gbk" /> 
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
<meta name="robots" content="all">
<meta name="author" content="Tencent-CP" />
<meta name="Copyright" content="Tencent" />
<meta name="Description" content="页面的描述内容" />
<meta name="Keywords" content="页面关键字" />
```
## M：
```html
<meta charset="gbk" /> 
<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no">
<!-- 为了防止页面数字被识别为电话号码，可根据实际需要添加： -->
<meta name="format-detection" content="telephone=no"> 
<!-- 让添加到主屏幕的网页再次打开时全屏展示，可添加：   -->
<meta content="yes" name="mobile-web-app-capable">
<meta content="yes" name="apple-mobile-web-app-capable">
<meta name="robots" content="all">
<meta name="author" content="Tencent-CP" />
<meta name="Copyright" content="Tencent" />
<meta name="Description" content="页面的描述内容" />
<meta name="Keywords" content="页面关键字" />
```
## meta标签大全详解：
```html
<meta charset="UTF-8">
//声明字符的编码**防止出现乱码

<meta http-equiv="x-UA-Compatible" content="IE=edge">
//避免IE使用兼容模式(必须放在前面否则无效)
 
<meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=no">
//对移动设备的友好 确保适当的绘制和触屏缩放 shrink-to-fit=no则禁用其缩放(zooming)功能*Bootstrap
 
<meta http-equiv="pragma" content="no-cache">
<meta http-equiv="Cache-Control" content="no-cache, must-revalidate">
<META http-equiv="expires" content="0">
//禁止html页面缓存

<meta name="author" content="作者">
//规定文档的作者
 
<meta name="description" content="页面描述">
//规定文档页面的描述(限150字符) 搜索引擎会把这个描述显示在搜索结果中
 
<meta name="keywords" content="关键字">
//搜索关键字用来告诉搜索引擎
 
<meta name="robots" content=" index,follow" />
//所有搜索引擎(搜索引擎抓取)
 
<meta name="googlebot" content="index,follow">
//搜索引擎抓取(只对谷歌有效)
 
<meta http-equiv=“expires” content=“Wed, 26 Feb 1997 08：21：57 GMT”>
//设定网页的到期时间。一旦网页过期，必须到服务器上重新调阅

<meta name="x5-orientation" content="portrait">
//QQ强制竖屏
 
<meta http-equiv="Cache-Control" content="no-transform" />
<meta http-equiv="Cache-Control" content="no-siteapp" />
//不让百度转码 原网页呈献给移动端

<meta http-equiv="Pragma" content="no-cache"> 
//禁止浏览器从本地机的缓存中调阅页面内容

<meta http-equiv="Window-target" content="_top">
//用来防止别人在框架里调用你的页面

<meta http-equiv="refresh" content="秒数,URL地址">
//规定几秒后跳转到指定的URL链接
 
<meta name="generator" content="FrontPage4.0">
//规定用于生成文档的一个软件包
 
<meta http-equiv="Content-Security-Policy" content="default-src 'self'">
//允许控制资源的过度加载
 
<meta name="application-name" content="应用名称">
//Web应用程序的名称(仅网站被用作一个应用时才使用它)
 
<meta name="google" content="nositelinkssearchbox">
//告诉Google不显示网站链接的搜索框信息
 
<meta name="google" content="notranslate">
//告诉Google不提供此页面的翻译
 
<meta name="google-site-verification" content="verification_token">
//验证 Google 搜索控制台的所有权
 
<meta name="yandex-verification" content="verification_token">
//验证 Yandex 网站管理员的所有权
 
<meta name="msvalidate.01" content="verification_token">
//验证 Bing 网站管理员中心的所有权
 
<meta name="alexaVerifyID" content="verification_token">
//验证 Alexa 控制台的所有权
 
<meta name="p:domain_verify" content="code from pinterest">
//验证 Pinterest 控制台的所有权
 
<meta name="norton-safeweb-site-verification" content="norton code">
//验证 Norton 安全站点的所有权
 
<meta name="generator" content="program">
//用来命名软件或用于构建网页（如WordPress、Dreamweaver）
 
<meta name="subject" content="主题描述">
//网站主题的简短描述
 
<meta name="abstract" content="">
// 非常简短(不大于10字)的描述。
 
<meta name="google" content="notranslate">
//禁用翻译提示（Google Chrome）
 
<meta name="rating" content="General">
//基于网站内容给出一般的年龄分级
 
<meta name="referrer" content="no-referrer">
//允许控制 referrer 信息如何传递
 
<meta name="format-detection" content="telephone=no">
//禁用自动检测和格式化可能的电话号码
 
<meta http-equiv="x-dns-prefetch-control" content="off">
//通过设置为 “off” 完全退出 DNS 预取
 
<meta http-equiv="set-cookie" content="name=value; expires=date; path=url">
//在客户端存储 cookie，web 浏览器的客户端识别
 
<meta http-equiv="Window-Target" content="_value">
//指定要显示在一个特定框架中的页面
 
<meta name="ICBM" content="latitude, longitude">
<meta name="geo.position" content="latitude;longitude">
//地理标签
 
<meta name="geo.region" content="country[-state]">
//国家代码 (ISO 3166-1): 强制性, 州代码 (ISO 3166-2): 可选; 如 content="US" / content="US-NY"
 
<meta name="geo.placename" content="city/town">
//如 content="New York City"
 
<meta name="apple-itunes-app" content="app-id=APP_ID,affiliate-data=AFFILIATE_ID,app-argument=SOME_TEXT">
//智能应用 Banner（apple IOS）
 
<meta name="format-detection" content="telephone=no">
//禁用自动检测和格式化可能的电话号码（apple IOS）
 
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black"> 
<meta name="apple-mobile-web-app-title" content="应用标题">
//添加到主屏幕（apple IOS）
 
<meta name="apple-itunes-app" content="app-id=APP-ID, app-argument=http/url-sample.com">
// iOS 应用深层链接（apple IOS）
 
<meta name="theme-color" content="#E64545">
//添加到主屏幕（Google Android）
 
<meta name="mobile-web-app-capable" content="yes">
//https://developer.chrome.com/multidevice/android/installtohomescreen（Google Android）
 
<meta name="mobile-web-app-capable" content="yes">
//定义你的网页为 Web 应用
 
<meta name="skype_toolbar" content="skype_toolbar_parser_compatible">
// IE10: 禁用链接点击高亮
 
<meta property="al:ios:url" content="applinks://docs">
<meta property="al:ios:app_store_id" content="12345">
<meta property="al:ios:app_name" content="App Links">
//应用链接（IOS）
 
<meta property="al:android:url" content="applinks://docs">
<meta property="al:android:app_name" content="App Links">
<meta property="al:android:package" content="org.applinks">
//应用链接（Android）
  
<meta name="wap-font-scale" content="no">
//禁用的UC浏览器的功能，“当此页面中有较多文本时缩放字体”（UC移动浏览器）
 
<meta name="screen-orientation" content="landscape/portrait">
//在指定方向上锁定屏幕 锁定横/竖屏（UC移动浏览器）
 
<meta name="full-screen" content="yes">
//全屏显示此页面（UC移动浏览器）
 
<meta name="imagemode" content="force">
//即使在“文本模式”下，UC浏览器也会显示图片（UC移动浏览器）
 
<meta name="browsermode" content="application">
//页面将以“应用模式”显示 全屏、禁止手势等（UC移动浏览器）
 
<meta name="nightmode" content="disable">
//在此页面禁用“夜间模式”（UC移动浏览器）
 
<meta name="layoutmode" content="fitscreen">
//简化页面 减少数据传输（UC移动浏览器）

<meta property="al:web:url" content="http://applinks.org/documentation">
//Web回退
 
<meta name="renderer" content="webkit|ie-comp|ie-stand">
//选择渲染引擎（360浏览器）
 
<meta name="x5-orientation" content="landscape/portrait">
//在指定方向上锁定屏幕 锁定横/竖屏（QQ移动浏览器）
 
<meta name="x5-fullscreen" content="true">
//全屏显示此页面（QQ移动浏览器）
 
<meta name="x5-page-mode" content="app">
//页面将以“应用模式”显示/全屏等（QQ移动浏览器）
```
