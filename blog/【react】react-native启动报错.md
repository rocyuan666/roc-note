## 安装app报错

运行安装app报错：react-native-gesture-handler...

![](assets/【react-native】启动报错/1.png)

运行 npx jetify 后重新安装即可

## 启动 js服务报错

打开 node_modules\graceful-fs\polyfills.js 文件，注释掉61~63行，重新启动即可

![](assets/【react-native】启动报错/2.png)

![](assets/【react-native】启动报错/3.png)
