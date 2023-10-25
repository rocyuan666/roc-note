# 下载
官网：[https://nginx.org/en/download.html](https://nginx.org/en/download.html)
```bash
wget https://nginx.org/download/nginx-1.22.1.tar.gz
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667280358070-b22fc53c-7b89-49b3-bf4a-b988a6d68497.png#averageHue=%23353331&clientId=u6a976d57-4d95-4&from=paste&height=303&id=u3b6bfd70&originHeight=303&originWidth=761&originalType=binary&ratio=1&rotation=0&showTitle=false&size=36894&status=done&style=none&taskId=u93a0cc67-d2ca-4af0-be39-18637e6a0a3&title=&width=761)
# 解压
```bash
tar zxvf nginx-1.22.1.tar.gz
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667280627261-c19554bd-bed7-451e-9d14-0ef6c6932cb4.png#averageHue=%2325211f&clientId=u6a976d57-4d95-4&from=paste&height=117&id=u8bb80e38&originHeight=117&originWidth=738&originalType=binary&ratio=1&rotation=0&showTitle=false&size=11573&status=done&style=none&taskId=udf44974f-6648-4af5-aaf6-b78b2257f60&title=&width=738)
# 安装
## 依赖准备
安装前需要安装nginx编译的依赖环境，依赖的名称在centos与ubuntu下，会有所不同，以下两种发行版都有。
整合全部依赖安装命令（执行后可直接跳至“编译安装”的步骤）
```bash
# centos
yum -y install make gcc-c++ zlib zlib-devel pcre pcre-devel openssl openssl-devel
# ubuntu
apt-get install make g++ zlib1g zlib1g.dev libpcre3 libpcre3-dev openssl libssl-dev
```
### make
编译安装必须需要make。make在centos与ubuntu下名称一样。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667281604773-cab6f93e-5c10-4bf1-b832-e6d891df2048.png#averageHue=%232e2624&clientId=u6a976d57-4d95-4&from=paste&height=128&id=u34d266c8&originHeight=128&originWidth=773&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20254&status=done&style=none&taskId=ud60e8d2d-bc46-47ae-9e96-192b3935048&title=&width=773)
### gcc-c++
GCC用来对nginx源码进行编译。
```bash
# centos
yum install gcc-c++
# ubuntu
apt-get install g++
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667281579393-e74bd725-3a80-4058-8527-7e551eaeb89e.png#averageHue=%23312724&clientId=u6a976d57-4d95-4&from=paste&height=99&id=tDrJc&originHeight=99&originWidth=744&originalType=binary&ratio=1&rotation=0&showTitle=false&size=16800&status=done&style=none&taskId=u08b8c0c8-6282-49f7-9d13-bdaf17ecb65&title=&width=744)
### zlib zlib-devel
zlib库提供了开发人员的压缩算法，在Nginx的各种模块中需要使用gzip压缩。
```bash
# centos
yum -y install zlib zlib-devel
# ubuntu
apt-get install zlib1g zlib1g.dev
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667281910971-bb4a0396-22ea-4276-92fe-2111a71c8dba.png#averageHue=%232c2624&clientId=u6a976d57-4d95-4&from=paste&height=528&id=u8f890e58&originHeight=528&originWidth=983&originalType=binary&ratio=1&rotation=0&showTitle=false&size=103577&status=done&style=none&taskId=uaee149f2-d62f-4af5-bbc6-ce2f55bef23&title=&width=983)
### pcre pcre-devel
Nginx的Rewrite模块和HTTP核心模块会使用到PCRE正则表达式语法。这里需要安装两个安装包pcre和pcre-devel。第一个安装包提供编译版本的库，而第二个提供开发阶段的头文件和编译项目的源代码。
```bash
# centos
yum -y install pcre pcre-devel
# ubuntu
apt-get install libpcre3 libpcre3-dev
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667282126647-1c70c472-46df-4a43-b4d5-920496a9c440.png#averageHue=%232a2523&clientId=u6a976d57-4d95-4&from=paste&height=735&id=u876f6fb9&originHeight=735&originWidth=1057&originalType=binary&ratio=1&rotation=0&showTitle=false&size=142645&status=done&style=none&taskId=udbac28cb-de71-49bc-9949-07dc6014736&title=&width=1057)
### openssl openssl-devel
nginx不仅支持 http协议，还支持 https（即在 ssl 协议上传输 http）。如果使用了 https，需要安装 OpenSSL 库。
```bash
# centos
yum -y install openssl openssl-devel
# ubuntu
apt-get install openssl libssl-dev
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667282756187-8e509637-5bbb-412f-a3a6-894955663cbf.png#averageHue=%232a2422&clientId=u6a976d57-4d95-4&from=paste&height=478&id=u890a2474&originHeight=478&originWidth=953&originalType=binary&ratio=1&rotation=0&showTitle=false&size=80628&status=done&style=none&taskId=uf8f77ee6-4c32-456c-90a7-7ff2b7a4697&title=&width=953)
## 编译安装
进入解压后的目录执行`./configure`，之后会生成Makefile文件
默认会安装在 `/usr/local/nginx` 可指定位置 `./configure --prefix=/home/rocyuan/software/nginx`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667283630029-24b7aff1-a861-4532-9856-eaa8ca076505.png#averageHue=%23262221&clientId=u6a976d57-4d95-4&from=paste&height=253&id=u1e2165dd&originHeight=253&originWidth=740&originalType=binary&ratio=1&rotation=0&showTitle=false&size=32585&status=done&style=none&taskId=ud01e92be-9bfc-46ce-b0c7-c5195d2b1a8&title=&width=740)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667283686566-1af78dea-c8a2-48fa-a13f-0418962282e4.png#averageHue=%23282524&clientId=u6a976d57-4d95-4&from=paste&height=110&id=uc8aab938&originHeight=110&originWidth=904&originalType=binary&ratio=1&rotation=0&showTitle=false&size=9212&status=done&style=none&taskId=u9009eeda-9f51-4fb3-99c9-2ec139b7dba&title=&width=904)
然后执行`make && make install`会进行编译安装。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667283758640-aad40614-0c0d-437f-8778-d5f24aec103d.png#averageHue=%23252221&clientId=u6a976d57-4d95-4&from=paste&height=218&id=u117faf22&originHeight=218&originWidth=927&originalType=binary&ratio=1&rotation=0&showTitle=false&size=30873&status=done&style=none&taskId=ud15c0c02-e219-42f3-8f9c-fe1e8cc266e&title=&width=927)
## 安装完成
安装完成后进入`/usr/local/nginx/sbin`下会有`nginx可执行文件`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667283916365-b2dda918-ffa4-4ace-855d-fd7bcc5a2088.png#averageHue=%232a2423&clientId=u6a976d57-4d95-4&from=paste&height=180&id=uaefcd9b1&originHeight=180&originWidth=584&originalType=binary&ratio=1&rotation=0&showTitle=false&size=9730&status=done&style=none&taskId=uf0ea9ce3-35b7-4a5c-8d7a-c30fef13bc3&title=&width=584)
然后访问`localhost`或者本机ip，会显示nginx的欢迎页
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667284060028-2374d7e2-5c70-4c3e-a3a1-89af0666fd2b.png#averageHue=%23272422&clientId=u6a976d57-4d95-4&from=paste&height=392&id=u37a9c51e&originHeight=392&originWidth=854&originalType=binary&ratio=1&rotation=0&showTitle=false&size=42965&status=done&style=none&taskId=u5658a272-a229-455e-b943-94de6e44537&title=&width=854)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667284140768-71a43676-c65f-4b16-8e99-aa0aa32cb4f0.png#averageHue=%23fdfdfc&clientId=u6a976d57-4d95-4&from=paste&height=599&id=u5d88de3b&originHeight=599&originWidth=1523&originalType=binary&ratio=1&rotation=0&showTitle=false&size=27451&status=done&style=none&taskId=u8c305390-67cc-49ed-a009-d0684dc60af&title=&width=1523)

