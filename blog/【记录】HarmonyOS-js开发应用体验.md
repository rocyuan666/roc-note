2020年9 月 10 日，华为开发者大会上，华为消费者业务 CEO 余承东正式发布了鸿蒙 OS 2.0 版本，并且宣布： 华为鸿蒙OS还将在 2020 年 12 月面向应用开发者发布手机版本；并且已经在gitee开源。
开源地址： [https://openharmony.gitee.com](https://openharmony.gitee.com/)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825739090-52e96206-7083-475f-abc3-b9807f4f1c28.png#clientId=ueb2c84af-e814-4&from=paste&id=ueb82d73d&originHeight=361&originWidth=698&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u70ffcd69-62f0-41f3-aa48-5e3596948d4&title=)
目前模拟器只有 TV 与 Wearable 两种；管他三七二十八先来体验下。。。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825738135-406b147f-a749-455e-a7b7-21fa4f7b49e2.png#clientId=ueb2c84af-e814-4&from=paste&id=ud47256a7&originHeight=414&originWidth=927&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u526f6d1e-5cb3-486c-be58-769711e1638&title=)
## 下载 DevEco Studio
DevEco Studio是面向华为终端全场景多设备的一站式分布式应用开发平台，支持分布式多端开发、分布式多端调测、多端模拟仿真。
下载地址：
[https://developer.harmonyos.com/cn/develop/deveco-studio#download](https://developer.harmonyos.com/cn/develop/deveco-studio#download)
安装就不演示了有手应该都会 ~ .~
## 新建js项目
安装好之后 新建项目 ；新建一个TV应用的js空项目，Next
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825738950-6a361209-0ef5-483f-8999-c41c5c277d74.png#clientId=ueb2c84af-e814-4&from=paste&id=ua359afeb&originHeight=713&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u507328b8-6731-4884-85a8-f93ea779d52&title=)
填写项目信息 完成
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825739104-f12c1895-8ae5-47b3-9c1d-e2ee706feb7d.png#clientId=ueb2c84af-e814-4&from=paste&id=u50b56d51&originHeight=705&originWidth=1014&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u7b4d6a4d-e653-4e80-81fe-c1af3814330&title=)
## 项目结构目录
很明显能看到，就是常规的前端MVVM框架
在工程目录中：common文件夹主要存放公共资源，如图片、视频等；i18n下存放多语言的json文件；pages文件夹下存放多个页面，每个页面由hml、css和js文件组成（前端三板斧）。 hml组件较少，后期也期待有大佬开发出ui组件库。文章末尾有官方开发文档传送门。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825738463-a87e1309-ee88-46b5-a632-62e4c3f254da.png#clientId=ueb2c84af-e814-4&from=paste&id=u5b4d7cea&originHeight=605&originWidth=403&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ude4db99a-88b6-4af2-99b5-b0d0d9c461a&title=)
## Hello World
美好的开端，Hello World，咱们更换下（Hello HarmonyOS App）。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825739465-98615eb0-4a2f-40f3-a2cb-a4dc9d41e01e.png#clientId=ueb2c84af-e814-4&from=paste&id=uc2a2f597&originHeight=156&originWidth=312&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u9daff366-de8a-4515-8529-a1bf32d0618&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825739730-4ed2458e-da84-4035-92ce-2c19c1b9f8e6.png#clientId=ueb2c84af-e814-4&from=paste&id=uab67e6b6&originHeight=212&originWidth=459&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ub29a90a8-e08c-44da-bfbf-d0da38887d0&title=)
## 运行应用
要运行应用我们需要安装模拟器
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825739935-e0b32e6e-d7d7-483e-8181-ac6fb211cf55.png#clientId=ueb2c84af-e814-4&from=paste&id=ub3da5d23&originHeight=366&originWidth=361&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u894be279-c2b3-44a2-98b4-0160d75258f&title=)
这时它会弹出网页让你登录华为开发者账号（没有的小伙伴自行申请认证），登录之后它会让你进行账号访问授权，允许后会登录DevEco Studio客户端；然后会下载模拟器（ TV 与 Wearable ）
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825739869-68582b3d-9b44-4494-825f-e3b43e2b36a5.png#clientId=ueb2c84af-e814-4&from=paste&id=u1f24e403&originHeight=614&originWidth=510&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ucc7a96c3-d9d7-4390-9726-3a5271a9014&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825740405-732b6b96-3745-4843-b999-86ed09a4575a.png#clientId=ueb2c84af-e814-4&from=paste&id=u971d91ef&originHeight=442&originWidth=522&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uadfd1888-5ae5-402a-a5ca-82e63a06a0a&title=)
看到这个界面说明下载成功，启动一个创建项目时所选择的设备（我选择TV）
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825740498-cfdb926d-7a17-4f0f-b6b8-896e120ac236.png#clientId=ueb2c84af-e814-4&from=paste&id=uff5cf659&originHeight=414&originWidth=927&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u46ec5f11-03c6-447f-bc3b-7248b676828&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825740655-fd2c1d6d-5f3b-43cd-a7e7-2ca7aff26fbe.png#clientId=ueb2c84af-e814-4&from=paste&id=ub685c709&originHeight=430&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u2835f041-2a41-4ad0-8ee1-cd7c613342f&title=)
然后点击运行，选择启动的模拟器
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825740681-0c2e4a0c-2a8c-4699-a60f-90d30079817e.png#clientId=ueb2c84af-e814-4&from=paste&id=u1f378b88&originHeight=226&originWidth=347&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u4add32d9-8295-4135-b4d7-6596b94caeb&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825741139-9d92c163-fb89-4276-b5b3-3d1f9caaa1f2.png#clientId=ueb2c84af-e814-4&from=paste&id=u8f3f5895&originHeight=591&originWidth=649&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u2a9ae101-86f7-4f84-bc14-a94e144e5d4&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825741635-2bde8ec8-080a-4b0f-b5e2-fc27d45793c4.png#clientId=ueb2c84af-e814-4&from=paste&id=u4db3df1d&originHeight=376&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u1cb00135-1a1b-4741-9a4e-25e13537623&title=)
即可看到运行结果
下面是 Wearable 演示
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825741340-024759e1-2c2d-4ff9-b440-5b99bcb0ae70.png#clientId=ueb2c84af-e814-4&from=paste&id=u1eac100c&originHeight=498&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ub2307125-b999-485e-ba14-aa6f6b67d06&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825741670-22d8ce87-0425-4099-8593-0803f3127037.png#clientId=ueb2c84af-e814-4&from=paste&id=u2e75ce5a&originHeight=460&originWidth=1024&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u52c6e732-b0e5-4078-9485-c1d0f521168&title=)
官方js开发文档
[https://developer.harmonyos.com/cn/docs/documentation/doc-guides/ui-js-overview-0000000000500376](https://developer.harmonyos.com/cn/docs/documentation/doc-guides/ui-js-overview-0000000000500376)
