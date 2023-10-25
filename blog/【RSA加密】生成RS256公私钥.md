使用JWT的时候用RS256进行签名；RS256 是使用 RSA 私钥进行签名，使用 RSA 公钥进行验证，公钥即使泄漏了也毫无影响，只要确保私钥的安全就行。
使用openssl生成RS256

- mac/linux 直接使用终端即可
- windows推荐在git bash终端中操作
```bash
# 生成1024位 RSA密钥
openssl genrsa -out private.key 1024
# 通过密钥生成公钥
openssl rsa -in private.key -pubout -out public.key
```
会在终端当前目录下生成公私钥。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667959140159-daa7cdb8-0572-49f4-a5c7-e2c9a98fe836.png#averageHue=%231e1b19&clientId=u10638df5-a45b-4&from=paste&height=297&id=u3c74f733&originHeight=297&originWidth=564&originalType=binary&ratio=1&rotation=0&showTitle=false&size=24001&status=done&style=none&taskId=uff762093-b42a-4e6f-80fe-d111597bf56&title=&width=564)
