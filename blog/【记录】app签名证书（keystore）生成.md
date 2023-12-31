## 安装jre环境

推荐jre8环境，环境变量记得配置（已安装的跳过）

## 生成签名证书

使用keytool -genkey命令生成证书：

```bash
keytool -genkey -alias testalias -keyalg RSA -keysize 2048 -validity 36500 -keystore test.keystore
```

- testalias是证书别名，可修改为自己想设置的字符，建议使用英文字母和数字
- test.keystore是证书文件名称，可修改为自己想设置的文件名称，也可以指定完整文件路径

回车后会提示：

```bash
Microsoft Windows [版本 10.0.18363.1379]
(c) 2019 Microsoft Corporation。保留所有权利。

E:\roc>keytool -genkey -alias rocalias -keyalg RSA -keysize 2048 -validity 36500 -keystore roc.keystore
输入密钥库口令:
再次输入新口令:
您的名字与姓氏是什么?
  [Unknown]:  rocyuan
您的组织单位名称是什么?
  [Unknown]:  hendon
您的组织名称是什么?
  [Unknown]:  hd
您所在的城市或区域名称是什么?
  [Unknown]:  shaanxi
您所在的省/市/自治区名称是什么?
  [Unknown]:  xian
该单位的双字母国家/地区代码是什么?
  [Unknown]:  CN
CN=rocyuan, OU=hendon, O=hd, L=shaanxi, ST=xian, C=CN是否正确?
  [否]:  y

输入 <rocalias> 的密钥口令
        (如果和密钥库口令相同, 按回车):
```

以上命令运行完成后就会生成证书，路径为“`E:\roc`”

![](assets/【安卓】app签名证书（keystore）生成/1.png)

## 查看证书信息

可以使用 `keytool -list -v -keystore roc.keystore` 命令查看证书信息


- roc.keystore是证书名

```bash
# 内容有删减，仅供参考

E:\roc>keytool -list -v -keystore roc.keystore
输入密钥库口令:
密钥库类型: jks
密钥库提供方: SUN

您的密钥库包含 1 个条目

别名: roc
创建日期: 2021-3-2
条目类型: PrivateKeyEntry
证书链长度: 1
证书[1]:
所有者: CN=rocyuan, OU=hendon, O=hd, L=shaanxi, ST=xian, C=CN
发布者: CN=rocyuan, OU=hendon, O=hd, L=shaanxi, ST=xian, C=CN
序列号: 4619c
有效期为 Tue Mar 02 10:31:11 CST 2021 至 Thu Feb 06 10:31:11 CST 2121
证书指纹:
         MD5:  2B:0A:42:46:62:64:E7:FD:24
         SHA1: C3:3A:0A:5B:A0:8D:83:C7:45:40:FE:88:2B:40:8E:1C
         SHA256: 8A:5C:C1:D1:CB:E5:88:35:97:64:04:02:DE:19:B7:A8
签名算法名称: SHA256withRSA
主体公共密钥算法: 2048 位 RSA 密钥
版本: 3

扩展:

#1: ObjectId: 2.5.29.14 Criticality=false
SubjectKeyIdentifier [
KeyIdentifier [
0000: AC 3D 78 E5 15 38 FB F0   CF E6 77 05 89 61 AA EF  .=x..8....w..a..
0010: 92 E0 DA 4F                                        ...O
]
]



*******************************************
*******************************************
```

## 安卓签名获取工具

安装配置证书的应用，然后安装使用签名获取工具获取该应用的签名。

工具下载地址参考：

[https://developers.weixin.qq.com/doc/oplatform/Downloads/Android_Resource.html](https://developers.weixin.qq.com/doc/oplatform/Downloads/Android_Resource.html)

![](assets/【安卓】app签名证书（keystore）生成/2.png)
