对于tp框架而言，自动生成的文件或者目录应该是runtime目录，所以在线部署代码的时候，开放此类目录的权限。
所以解决mkdir() premission denied 的问题最直接的方式，把runtime权限放开，让所有用户都可以创建它。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825953784-2301ef74-2e99-492a-9d09-c4e8fa3ddc6d.png#clientId=u18e2db26-58b8-4&from=paste&id=u54771578&originHeight=503&originWidth=711&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u2a3de8e4-14f9-44f6-b600-6bd3ee17f9d&title=)
在runtime同级目录下执行
chmod -R 777 runtime
或者宝塔修改权限777
即可成功访问！
