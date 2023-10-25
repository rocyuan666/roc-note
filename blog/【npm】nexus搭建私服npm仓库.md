# 下载nexus
官网下载：[https://help.sonatype.com/repomanager3/product-information/download/download-archives---repository-manager-3](https://help.sonatype.com/repomanager3/product-information/download/download-archives---repository-manager-3)
百度网盘下载：[https://pan.baidu.com/s/1INXWe37DJTtcHTTTFPedsQ](https://pan.baidu.com/s/1INXWe37DJTtcHTTTFPedsQ) 提取码：1qwi
# 安装
下载完后进行解压 `tar -zxvf nexus-3.21.2-03-unix.tar.gz`
进入解压后目录 nexus-3.21.2-03/bin 运行`./nexus`，会提示nexus的命令`Usage: ./nexus {start|stop|run|run-redirect|status|restart|force-reload}`
启动运行`./nexus start`
查看状态`./nexus status`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661523250740-d6d6b823-022a-4153-8793-a743001d68f6.png#clientId=ue66df182-f208-4&from=paste&height=260&id=ud0539a6b&originHeight=260&originWidth=819&originalType=binary&ratio=1&rotation=0&showTitle=false&size=36977&status=done&style=none&taskId=uf5bc5803-af8c-4308-95ba-49a73bc6114&title=&width=819)
`./nexus status`是看不到打印日志的；使用`./nexus run`可以看到打印日志。
# 配置文件
配置文件是`nexus-3.21.2-03/etc/nexus-default.properties` 可以看到默认配置端口是8081
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661523554309-48f7c53a-fcfd-4351-bde9-09de75064134.png#clientId=ue66df182-f208-4&from=paste&height=326&id=ue5c887ae&originHeight=326&originWidth=782&originalType=binary&ratio=1&rotation=0&showTitle=false&size=35444&status=done&style=none&taskId=u88ea7f92-16e7-482d-afa2-5231acdd347&title=&width=782)
# 访问
访问`ip:8081`即可访问，打不开的请检查端口是否开放，服务器配置安全组。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661566662739-9c2d3884-e667-46f9-84ba-6e28405e353e.png#clientId=uc45df573-50b7-4&from=paste&height=1048&id=u21d34889&originHeight=1048&originWidth=1859&originalType=binary&ratio=1&rotation=0&showTitle=false&size=42169&status=done&style=none&taskId=u1202a516-4e62-4be8-9d0f-2c377505f1e&title=&width=1859)
# 登录
登录管理员，用户名为：admin密码存放在`sonatype-work/nexus3/admin.password`；登录后根据提示设置新密码。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661566859324-e93d2260-8949-4f73-beb3-8c6d17ead778.png#clientId=uc45df573-50b7-4&from=paste&height=315&id=ud655f646&originHeight=315&originWidth=543&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13026&status=done&style=none&taskId=u84ccbaba-abf4-4c12-810e-6349372d4b5&title=&width=543)
# 创建npm仓库
创建顺序：

1. npm(proxy) 代理仓库 可以设置官方源或者镜像源
2. npm(hosted) 本地仓库
3. npm(group) 组仓库

![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661567029931-030bc259-e846-4451-aea7-2f9210577c2b.png#clientId=uc45df573-50b7-4&from=paste&height=1009&id=ue2ae567c&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=100328&status=done&style=none&taskId=udf8c0ae0-5778-4840-a9d6-652f025d6d8&title=&width=1858)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661567118274-fc272d14-9153-4342-adc0-1d32698b3a6a.png#clientId=uc45df573-50b7-4&from=paste&height=1009&id=u78b23422&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=129396&status=done&style=none&taskId=u8d9933fc-af23-49dd-a753-e1a7963054f&title=&width=1858)
# 创建npm代理仓库
填写仓库唯一标识（名称）和源地址，其他默认，点击创建仓库(Create repository)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661567565819-b92b32b6-ddb3-4852-a562-dcc86d3ea309.png#clientId=uc45df573-50b7-4&from=paste&height=1009&id=u83b4806a&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=115062&status=done&style=none&taskId=u692ecbd5-9087-4696-a1c2-ca47d045abd&title=&width=1858)
# 创建npm本地仓库
填写仓库唯一标识（名称）和设置允许重新部署，其他默认，点击创建仓库(Create repository)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661567840990-08f665c1-7926-4efb-8757-0701fc5ce314.png#clientId=uc45df573-50b7-4&from=paste&height=1009&id=ub5a9d3b5&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=91787&status=done&style=none&taskId=uf5ded6fb-276b-490d-b39a-be832bdb6b0&title=&width=1858)
# 创建npm组仓库
填写仓库唯一标识（名称）和设置之前创建的本地仓库和代理仓库（注意优先级，优先本地仓库，其次代理仓库），其他默认，点击创建仓库(Create repository)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661568030349-5717518c-f4ff-4b4f-a264-30ee1a92c603.png#clientId=uc45df573-50b7-4&from=paste&height=1009&id=uaf6164bb&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=99463&status=done&style=none&taskId=ue34eeeb8-bf66-4e85-9f8f-9793d319416&title=&width=1858)
# 创建完成
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661568233908-56335015-2927-4643-962f-739dfe6417be.png#clientId=uc45df573-50b7-4&from=paste&height=1009&id=u76ae5376&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=110866&status=done&style=none&taskId=uc12809a6-4823-4dc3-b8ef-e2af4f87c57&title=&width=1858)
# 设置npm使用创建的npm-group源
```bash
# 设置源
npm config set registry=http://192.168.10.15:8081/repository/npm-group/
#查看源
npm config get registry
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661568701214-82078841-ac9e-44e5-8ee0-92453f8b971f.png#clientId=uc45df573-50b7-4&from=paste&height=176&id=u687f0317&originHeight=176&originWidth=817&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8370&status=done&style=none&taskId=u3d3de662-b886-4bed-a32d-0e33f4f19a9&title=&width=817)
# npm安装
以安装vue为例，安装完成后会被拉取到自己服务器上，下次安装就会优先使用本地仓库。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661569672016-d825b17a-e842-45c9-96f1-8cc1d45082ee.png#clientId=uc45df573-50b7-4&from=paste&height=268&id=u0a61d5fd&originHeight=268&originWidth=627&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14848&status=done&style=none&taskId=u8c9d0d8a-7369-48cb-b7e4-d7800c8adac&title=&width=627)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661569761286-8ebbfecf-09b2-411e-9dd9-925ff02e1680.png#clientId=uc45df573-50b7-4&from=paste&height=1009&id=u05ac1757&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=53446&status=done&style=none&taskId=u016146d7-c531-4bb0-b3f9-149bcc12356&title=&width=1858)
# 发布npm私有包
## 注册用户
发布前需要在命令行登录（建议新建用户登录），可以创建角色（我这块使用admin角色）
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661572269279-de8433d3-edc7-4d2f-b42b-74c63b5e7e35.png#clientId=u73ca7042-48ed-4&from=paste&height=1009&id=u049dd0db&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=87397&status=done&style=none&taskId=uaa139095-a872-47e6-a269-89ef532f8a0&title=&width=1858)
## 命令行登录
注意：登录的时候需要指定本地仓库源
```bash
npm login --registry=http://192.168.10.15:8081/repository/npm-hosted/
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661572637149-fc2825cb-79b3-41f5-b17a-61a53663cdf4.png#clientId=u73ca7042-48ed-4&from=paste&height=202&id=uc16b314b&originHeight=202&originWidth=670&originalType=binary&ratio=1&rotation=0&showTitle=false&size=14102&status=done&style=none&taskId=u07e5a361-f647-44b4-b968-02fd152cbdd&title=&width=670)
## 发布包
发布前需要添加`npm Bearer Token Realm`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661573208455-78dc9fdc-b4ce-4756-bafd-9b23711aeed4.png#clientId=u73ca7042-48ed-4&from=paste&height=1009&id=uf36debfd&originHeight=1009&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=100403&status=done&style=none&taskId=uee6babd5-8af8-4e4d-8566-afa1fa7c116&title=&width=1858)
创建项目`npm init -y`随便写个测试包，我起的名字为：`npmtest`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661572891607-57459162-cd35-4a16-be57-dffb6961761c.png#clientId=u73ca7042-48ed-4&from=paste&height=272&id=uc95eb667&originHeight=272&originWidth=660&originalType=binary&ratio=1&rotation=0&showTitle=false&size=18774&status=done&style=none&taskId=ud8bed4f4-2d18-4a03-b0c2-cb5171993ea&title=&width=660)
发布
```bash
npm publish --registry=http://192.168.10.15:8081/repository/npm-hosted/
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661573315989-ddb0f0fb-da35-4a37-bc9e-e4a1df5cfbe7.png#clientId=u73ca7042-48ed-4&from=paste&height=304&id=ue3d5334c&originHeight=304&originWidth=664&originalType=binary&ratio=1&rotation=0&showTitle=false&size=27893&status=done&style=none&taskId=u3efab93a-d0ed-42c4-a40c-bedd415a8e0&title=&width=664)
# 测试引入刚才发布的私有包
创建一个项目（rocyuan666）`npm install npmtest`引入npmtest；打印出了npmtest包中的打印
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1661573836610-73954ef4-fd27-4fe5-bbaf-710b32a6977e.png#clientId=u73ca7042-48ed-4&from=paste&height=1080&id=u93428d8c&originHeight=1080&originWidth=1858&originalType=binary&ratio=1&rotation=0&showTitle=false&size=120921&status=done&style=none&taskId=u9701e6f0-fbd8-4be5-9227-4e0e9352af6&title=&width=1858)
