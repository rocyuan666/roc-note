本人网站已设置为https协议，github上项目，接口等地址延迟同步，本文章记录下升https配置所需步骤

### 1.准备ssl

申请ssl证书：[https://freessl.cn/](https://freessl.cn/)

或者腾讯云，阿里云中申请，以阿里为例，进入 ssl证书(应用安全)，选择免费的ssl证书申请

![](assets/【记录】apache配置SSL证书/1.png)

申请成功后：

![](assets/【记录】apache配置SSL证书/2.png)

点击右侧下载，下载对应的服务器类型证书，我用的Apache，下载后的文件（三个）

- .key文件是证书私钥文件，如果申请证书时没有选择系统创建CSR，则没有该文件。请您保存好该私钥文件。
- .crt文件是证书文件，一般包含两段内容。如果是Apache服务器，会将证书文件拆分成 _public.crt（证书文件）和_chain.crt（证书链或中间证书文件）。
- .pem文件是证书文件，一般包含两段内容。Nginx证书会使用扩展名文件，在阿里云SSL证书中与.crt文件一样。
- .pfx文件，一般适合Tomcat/IIS服务器。每次下载都会产生新密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新密码。

![](assets/【记录】apache配置SSL证书/3.png)

![](assets/【记录】apache配置SSL证书/4.png)

### 2.部署证书

将证书放到：Apache目录下的cert目录下（ cert目录需要自行创建）

![](assets/【记录】apache配置SSL证书/5.png)

### 3.修改配置文件

1）打开 apache 安装目录下 conf 目录中的 httpd.conf 文件，找到以下内容并去掉注释“#”：

```css
#LoadModule ssl_module modules/mod_ssl.so
#Include conf/extra/httpd-ssl.conf
```

![](assets/【记录】apache配置SSL证书/6.png)

2） 把httpd-ssl.conf文件清空了，复制一下内容，修改 文档的路径和域名信息，保存。

```
Listen 443
<VirtualHost *:443>
	DocumentRoot "C:\phpStudy\PHPTutorial\WWW\www.luojing.top"
	ServerName www.luojing.top

	ServerAlias luojing.top
	SSLEngine on

	# 添加 SSL 协议支持协议，去掉不安全的协议
	SSLProtocol all -SSLv2 -SSLv3
	# 修改加密套件如下
	SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM
	SSLHonorCipherOrder on
	# 证书公钥配置
	SSLCertificateFile "C:\phpStudy\PHPTutorial\Apache\cert\3786809_luojing.top_public.crt"
	# 证书私钥配置
	SSLCertificateKeyFile "C:\phpStudy\PHPTutorial\Apache\cert/3786809_luojing.top.key"
	# 证书链配置，如果该属性开头有 '#'字符，请删除掉
	SSLCertificateChainFile "C:\phpStudy\PHPTutorial\Apache\cert/3786809_luojing.top_chain.crt"

	<Directory "C:\phpStudy\PHPTutorial\WWW\www.luojing.top">
		Options +Indexes +FollowSymLinks +ExecCGI
		AllowOverride All
		Order allow,deny
		Allow from all
		Require all granted
	</Directory>

</VirtualHost>
```

重启服务器 ok

