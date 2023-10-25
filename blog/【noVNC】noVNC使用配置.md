# 准备工作
git、node安装省略...
UltraVNC VNC server 下载地址
[https://uvnc.com/](https://uvnc.com/)
noVNC项目 git地址
[https://github.com/novnc/noVNC](https://github.com/novnc/noVNC)
noVNC所需WebSocket项目 git地址
[https://github.com/novnc/websockify-js](https://github.com/novnc/websockify-js)
# 安装UltraVNC
安装VNC服务，next......
![image.png](https://cdn.nlark.com/yuque/0/2023/png/2779910/1690255804353-3be48272-7602-4d01-a8cf-7773ea1630f7.png#averageHue=%23f1efed&clientId=u82918d6b-c561-4&from=paste&height=388&id=u63919566&originHeight=388&originWidth=503&originalType=binary&ratio=1&rotation=0&showTitle=false&size=39851&status=done&style=none&taskId=uddd63f31-40b7-456f-9af5-1028acf3796&title=&width=503)
安装完成运行VNC server，右键右下角，可设置密码、端口等。。。
![image.png](https://cdn.nlark.com/yuque/0/2023/png/2779910/1690255960218-1ba3cccd-fce3-48c1-b2b9-710eb27903e6.png#averageHue=%23f9efec&clientId=u82918d6b-c561-4&from=paste&height=168&id=uf6a7f845&originHeight=168&originWidth=235&originalType=binary&ratio=1&rotation=0&showTitle=false&size=9009&status=done&style=none&taskId=u13769b96-c06c-4085-ae27-b31f47e6b59&title=&width=235)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/2779910/1690255943144-3a334c1a-f47b-44c1-a3d2-a640292b17a2.png#averageHue=%23bfa879&clientId=u82918d6b-c561-4&from=paste&height=424&id=u86210bc4&originHeight=424&originWidth=371&originalType=binary&ratio=1&rotation=0&showTitle=false&size=40177&status=done&style=none&taskId=ud70e0337-7bd5-4977-b1a5-0823e555d13&title=&width=371)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/2779910/1690256021276-702f0468-9587-4d8c-91c0-450752afa8c7.png#averageHue=%23e6e3e1&clientId=u82918d6b-c561-4&from=paste&height=534&id=u4d3f6363&originHeight=534&originWidth=591&originalType=binary&ratio=1&rotation=0&showTitle=false&size=57692&status=done&style=none&taskId=u5ef92d0f-1826-4e00-bb95-685f375f358&title=&width=591)
# 克隆项目
noVNC 和 websockify-js项目克隆完成后，进入websockify-js项目中的websockify目录安装依赖。修改websockify.js 中 filename拼接访问的html。
![image.png](https://cdn.nlark.com/yuque/0/2023/png/2779910/1690256481656-d7b19c3d-006b-442b-b1eb-2743645a9fde.png#averageHue=%23947e47&clientId=u82918d6b-c561-4&from=paste&height=836&id=u3fd34ceb&originHeight=836&originWidth=1021&originalType=binary&ratio=1&rotation=0&showTitle=false&size=131833&status=done&style=none&taskId=uc9f651d2-ef68-45a6-9ba9-c87af5c95fc&title=&width=1021)
# 运行
说明见上图（完整功能需要指定 pem及key）
```bash
node websockify.js --web ../../noVNC-1.4.0/ 9000 localhost:5900
```
# 访问
输入VNC服务设置的密码进入
![image.png](https://cdn.nlark.com/yuque/0/2023/png/2779910/1690256683168-4077c5a8-2ca0-483d-a78e-927f583f56cd.png#averageHue=%23383838&clientId=u82918d6b-c561-4&from=paste&height=1047&id=u6b5dbd97&originHeight=1047&originWidth=1915&originalType=binary&ratio=1&rotation=0&showTitle=false&size=64287&status=done&style=none&taskId=ua7c73e1b-4925-42a0-9715-0213edbe7cd&title=&width=1915)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/2779910/1690256761909-7e797d16-d5e2-4902-8491-7cdb2900b952.png#averageHue=%23514937&clientId=u82918d6b-c561-4&from=paste&height=1044&id=ucdb951d0&originHeight=1044&originWidth=1916&originalType=binary&ratio=1&rotation=0&showTitle=false&size=727665&status=done&style=none&taskId=u001ab2f4-2455-47c6-ba52-2b74b9ceca0&title=&width=1916)
