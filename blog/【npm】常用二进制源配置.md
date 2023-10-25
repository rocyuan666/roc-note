npm配置都在`~/.npmrc`，修改`~/.npmrc`文件即可。
也可使用命令：
```bash
npm config set xxx 源地址
```
# 介绍
```bash
# npm源地址
registry=https://registry.npmmirror.com/
# node-sass依赖
sass_binary_site=https://npmmirror.com/mirrors/node-sass/
# weex项目依赖phantomjs-prebuilt
phantomjs_cdnurl=https://npmmirror.com/mirrors/phantomjs/
# electron依赖
electron_mirror=https://npmmirror.com/mirrors/electron/
# sqlite3轻量级数据库依赖
sqlite3_binary_host_mirror=http://npmmirror.com/mirrors/
# node-inspector依赖
profiler_binary_host_mirror=http://npmmirror.com/mirrors/node-inspector/
# chromedriver安装失败
chromedriver_cdnurl=https://npmmirror.com/mirrors/chromedriver
# sentry-cli依赖
sentrycli_cdnurl=https://npmmirror.com/mirrors/sentry-cli/
```
# 配置
`.npmrc`文件
linux位置：/home/rocyuan(自己的用户)/.npmrc  （~/.npmrc）
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1669260833298-7ef9b9c5-063f-4144-ab56-16bb385eee8d.png#averageHue=%230e0c0b&clientId=ueaf7985b-00a6-4&from=paste&height=238&id=qdtIZ&originHeight=238&originWidth=972&originalType=binary&ratio=1&rotation=0&showTitle=false&size=25671&status=done&style=none&taskId=u7a229a6f-ba7b-4119-85a6-4077241f05a&title=&width=972)
windows位置：C:\Users\Administrator(自己的用户)\.npmrc
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1669260716466-81fbb6d1-f4f3-47ad-9da1-e2ab99f2d57e.png#averageHue=%23f9f4f3&clientId=ueaf7985b-00a6-4&from=paste&height=169&id=ua594e29f&originHeight=169&originWidth=301&originalType=binary&ratio=1&rotation=0&showTitle=false&size=7265&status=done&style=none&taskId=u5968aa36-6c52-4647-9222-df30144b5fa&title=&width=301)
```bash
registry=https://registry.npmmirror.com/
sass_binary_site=https://npmmirror.com/mirrors/node-sass/
phantomjs_cdnurl=https://npmmirror.com/mirrors/phantomjs/
electron_mirror=https://npmmirror.com/mirrors/electron/
sqlite3_binary_host_mirror=http://npmmirror.com/mirrors/
profiler_binary_host_mirror=http://npmmirror.com/mirrors/node-inspector/
chromedriver_cdnurl=https://npmmirror.com/mirrors/chromedriver
sentrycli_cdnurl=https://npmmirror.com/mirrors/sentry-cli/
```
