对于tp框架而言，自动生成的文件或者目录应该是runtime目录，所以在线部署代码的时候，开放此类目录的权限。
所以解决mkdir() premission denied 的问题最直接的方式，把runtime权限放开，让所有用户都可以创建它。

![](assets/【tp5】TP5_Linux下Permission_denied/1.png)

在runtime同级目录下执行
`chmod -R 777 runtime`
或者宝塔修改权限777
即可成功访问！
