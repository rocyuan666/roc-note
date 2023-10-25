在vue脚手架中我们需要配置webpack，可在根目录创建vue.config.js文件进行配置，但是在react脚手架中并不支持react.config.js进行配置。
## yarn eject 弹出配置文件（慎操！！！不推荐）
react中要配置webpack我们可以运行 yarn eject 暴露所有配置
yarn eject之前的目录
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840559884-572dc429-4e3c-47a4-a176-4322ce7d9c2e.png#clientId=u1831f61d-4a9a-4&from=paste&id=ue071b767&originHeight=230&originWidth=215&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ua2080a31-c916-464c-9011-d39145818b8&title=)
yarn eject时它会提示你：您确定要弹出吗？此动作是永久性的。
意思就是执行 yarn eject 弹出配置后，是不可逆的。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840559866-8cbc40ec-3857-4cc0-a1bf-9c05e8281cc2.png#clientId=u1831f61d-4a9a-4&from=paste&id=u16a992d3&originHeight=195&originWidth=521&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ua7747a5a-7b3e-45de-94db-a6133e71a43&title=)
yarn eject 之后的目录
暴露出来配置文件后即可进行配置（谨慎操作！！！不推荐）
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840559887-da4b64c2-fad6-4037-bd5b-99b3ad31d2bd.png#clientId=u1831f61d-4a9a-4&from=paste&id=u106513f8&originHeight=534&originWidth=259&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u8a23aeec-af49-42bc-8ec6-610d7ec6687&title=)
## craco使用（推荐）
使用craco进行配置，我们并不需要yarn eject弹出配置文件
安装craco：yarn add @craco/craco
在根目录创建：craco.config.js
package.json文件中启动项目的脚本更改：react-scripts 更改为 craco
更改的作用是什么？请补习npm知识：[https://luojing.top/?p=1383](https://luojing.top/?p=1383)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840560056-342c3878-5c86-4634-ab03-f751ec9fdb9f.png#clientId=u1831f61d-4a9a-4&from=paste&id=u0f83e8b6&originHeight=339&originWidth=591&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uf2a8be20-bd27-4558-a85c-0f41e2ca636&title=)
然后在craco.config.js文件中进行webpack配置即可。
参考：[https://www.npmjs.com/package/@craco/craco](https://www.npmjs.com/package/@craco/craco)
