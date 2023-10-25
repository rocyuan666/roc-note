一般在开发小程序的时候，一不小心就会造成包大小超过2m无法上传，一般处理方法就是图片方面的优化（放在服务器，图片压缩…），删除无用代码（uniapp打包后会分析依赖的代码，删除无用代码），再就是分包加载处理。
常开发的是微信小程序，以下都以微信小程序为例
## 分包加载介绍
在构建小程序分包项目时，则会输出一个或多个分包。每个有分包的小程序必定含有一个**主包（也就是在/pages下）**。通常在主包下放置默认启动页面及tabBar 页面，以及一些所有分包都需用到公共资源（自定义组件、js工具代码、图片等）；而**分包**则是根据开发者的配置进行划分。
小程序启动时，默认会下载主包并启动主包内页面，当用户点击进入分包内某个页面时，客户端会把对应的分包下载下来，下载完成后再进行展示。
## 开启分包
在uniapp中开启分包时需要在对应的平台开启分包，开启分包的配置在manifest.json文件中，打开文件后HBuilderX会显示视图界面，但是选择**微信小程序配置**是没有开启分包的配置。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468106181-1f500694-1d03-4bf5-b02a-d37f8c4862cc.png#clientId=u39f685b0-1302-4&from=paste&id=u208e19ec&originHeight=492&originWidth=656&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u7726f0ca-f096-4c22-a0d6-1a08fa80683&title=)
无分包配置
需要点击最下面的源码试图，在json中配置，打开后找到mp-weixin选项（/* 小程序特有相关 */）添加"optimization":{"subPackages":true}，至此已经在微信小程序平台打开了分包配置。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468105746-bdc924e8-911b-46c7-a473-5c5005d67f66.png#clientId=u39f685b0-1302-4&from=paste&id=u6d9737dd&originHeight=385&originWidth=665&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u20dafb0a-7027-4f26-8e25-b42bcd18a99&title=)
添加分包配置
## 配置分包
目前为止（2021-09-09），uniapp只支持mp-weixin、mp-qq、mp-baidu、mp-toutiao开启分包加载。多平台编译的话需要写条件编译进行判断环境。
在pages.json文件中根层级（与”pages”选项同级）添加：
"subPackages": [{     "root": "rocA",     "pages": [{         "path": "roc/roc"     }] }]
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468106353-ebe2965a-6e31-4ab2-a40c-5f780e578491.png#clientId=u39f685b0-1302-4&from=paste&id=ub7cb4ef0&originHeight=739&originWidth=637&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u6cc9a610-c337-43a1-b995-6a44479984b&title=)
分包配置对应的目录
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468105766-875a48c9-b350-41c8-b873-4e2533f649d9.png#clientId=u39f685b0-1302-4&from=paste&id=u63132978&originHeight=704&originWidth=882&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ud1e7ee99-c412-46e3-99dd-adc2a1aaaf4&title=)
如上图可以有多个分包，但是微信小程序规定：

- 整个小程序所有分包大小不超过 20M
- 单个分包/主包大小不能超过 2M
## 分包效果
在微信开发工具中打开代码依赖分析视图可看到，已经分有一个主包和两个分包（rocA、rocB）
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468105205-b88fcb80-aaa9-4f53-ac63-43ccbc4c8359.png#clientId=u39f685b0-1302-4&from=paste&id=ud4ee404c&originHeight=512&originWidth=960&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u6d5bdf20-5936-4ff6-8c56-3497b35587f&title=)
## 主包分包页面之间转跳
转跳与平时一样写路径转跳就行，个人推荐第一种，如下：
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468107368-d9f37081-bb36-4fb1-a6c9-2e4e38892303.png#clientId=u39f685b0-1302-4&from=paste&id=uf75b8271&originHeight=504&originWidth=541&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ue4aa8626-1b25-446a-b503-3d5dbd63ff1&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468107923-dad41ff4-e25b-44f5-b409-9cb928e9bcd7.png#clientId=u39f685b0-1302-4&from=paste&id=ua5244031&originHeight=215&originWidth=754&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u33d7482e-0e32-4521-b40a-c31be61f000&title=)
## 分包资源
资源（图片、自定义组件、js工具代码）构建在分包中时，只能在分包使用不能在主包中使用；在主包里的资源主包分包都能使用，相当于公共资源。**我这里只列举图片资源**，其他的同理。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468108161-bd8d7874-907e-46dc-8c9b-925cf2c435ce.png#clientId=u39f685b0-1302-4&from=paste&id=ud380e724&originHeight=349&originWidth=336&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u0e7e373d-4c9c-48db-bb3c-6b428e67bcb&title=)
### 在分包中应用的图片资源
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468108840-dbf3e177-eb2a-452c-a1c6-2279ef0f7886.png#clientId=u39f685b0-1302-4&from=paste&id=u72e314b7&originHeight=672&originWidth=816&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u097c76eb-2812-4632-a399-a3edfdf9dc2&title=)
### 在主包中应用的图片资源
roc.jpg是在rocA分包下，所以主包不能使用，报错提示：
**项目资源 rocA/static/roc.jpg 与页面不在同一个分包中导致无法正常加载**
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468109582-c14398c6-136f-4642-b033-96bd4a9fb82c.png#clientId=u39f685b0-1302-4&from=paste&id=ua4a0cdc8&originHeight=448&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uf46b3b21-77d5-463c-98ec-6f5d1f8e5f5&title=)
## 查看资源所在的包
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1632468110903-e3ef7285-08d3-436a-82ac-e55a8afcc55b.png#clientId=u39f685b0-1302-4&from=paste&id=u6e7b9776&originHeight=512&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u938d8e9b-00ad-4270-a4c9-a43bab4e29e&title=)
一般建议项目初期就规划好分包构建，通常启动页与tabbar页面及公共组件、js工具、图片等公用的资源在主包，其他的可按照功能模块划分分包。
