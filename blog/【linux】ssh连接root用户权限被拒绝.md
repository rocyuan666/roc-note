# 连接错误
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1660816157274-216dafe7-9f2d-464e-8a01-fd6cffa7ff35.png#clientId=ue0557868-5ad8-4&from=paste&height=94&id=u8670972f&originHeight=94&originWidth=753&originalType=binary&ratio=1&rotation=0&showTitle=false&size=4683&status=done&style=none&taskId=uf32204d7-01aa-44c9-a4a0-204983dca3a&title=&width=753)
# 解决方案
修改`/etc/ssh/sshd_config`文件
```css
PermitRootLogin yes
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1660816411168-07e4072a-3867-41f5-ba39-75a3ae60c823.png#clientId=ue0557868-5ad8-4&from=paste&height=102&id=u83fa1990&originHeight=102&originWidth=963&originalType=binary&ratio=1&rotation=0&showTitle=false&size=10249&status=done&style=none&taskId=uc99f439b-6339-4d73-b7e4-2187dd05db8&title=&width=963)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1660816805491-a5a669b5-80cc-453d-97cc-48ed848d78ee.png#clientId=ue0557868-5ad8-4&from=paste&height=641&id=u2cac8456&originHeight=641&originWidth=875&originalType=binary&ratio=1&rotation=0&showTitle=false&size=46393&status=done&style=none&taskId=u4a50fd22-5b8c-4f27-bd90-c5480e45960&title=&width=875)
修改完重启下即可
```css
systemctl restart sshd
```
# 连接成功
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1660816933645-afa4b259-8cd9-47dd-87a3-f5de890be775.png#clientId=ue0557868-5ad8-4&from=paste&height=288&id=uf05fdbce&originHeight=288&originWidth=752&originalType=binary&ratio=1&rotation=0&showTitle=false&size=10522&status=done&style=none&taskId=u925d2805-ef03-4c44-aa7f-70c2a65772e&title=&width=752)
