## 安装app报错
运行安装app报错：react-native-gesture-handler...
![image.png](https://cdn.nlark.com/yuque/0/2021/png/2779910/1636114118080-21a3f82f-ac99-44bf-afd4-28066a7f735d.png#clientId=u824a4858-ddc2-4&from=paste&height=365&id=u57972c6f&originHeight=365&originWidth=1064&originalType=binary&ratio=1&rotation=0&showTitle=false&size=39786&status=done&style=none&taskId=u04fb9c56-c7ea-4a86-92b8-005d2587955&title=&width=1064)
运行 npx jetify 后重新安装即可

## 启动 js服务报错
打开 node_modules\graceful-fs\polyfills.js 文件，注释掉61~63行，重新启动即可
![image.png](https://cdn.nlark.com/yuque/0/2021/png/2779910/1636093913343-982aa2ab-9cea-4dd2-be2e-c9c563ee29a9.png#clientId=uae114dff-6226-4&from=paste&height=187&id=u9e8f86a1&originHeight=187&originWidth=919&originalType=binary&ratio=1&rotation=0&showTitle=false&size=21316&status=done&style=none&taskId=ua84876a4-226a-42ac-8e8f-d4131719652&title=&width=919)
![image.png](https://cdn.nlark.com/yuque/0/2021/png/2779910/1636093833559-88343de4-9081-43c2-9e28-c9e26b38f138.png#clientId=uae114dff-6226-4&from=paste&height=662&id=u72a7d6ae&originHeight=662&originWidth=849&originalType=binary&ratio=1&rotation=0&showTitle=false&size=70778&status=done&style=none&taskId=u01fb13ad-2ca1-42e4-a9da-9c9264b038d&title=&width=849)
