# 下载
官网：[https://nginx.org/en/download.html](https://nginx.org/en/download.html)
```bash
wget https://nginx.org/download/nginx-1.22.1.tar.gz
```
![](assets/【nginx】linux(centos&ubuntu)安装nginx/1.png)
# 解压
```bash
tar zxvf nginx-1.22.1.tar.gz
```
![](assets/【nginx】linux(centos&ubuntu)安装nginx/2.png)
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
![](assets/【nginx】linux(centos&ubuntu)安装nginx/3.png)
### gcc-c++
GCC用来对nginx源码进行编译。
```bash
# centos
yum install gcc-c++
# ubuntu
apt-get install g++
```
![](assets/【nginx】linux(centos&ubuntu)安装nginx/4.png)
### zlib zlib-devel
zlib库提供了开发人员的压缩算法，在Nginx的各种模块中需要使用gzip压缩。
```bash
# centos
yum -y install zlib zlib-devel
# ubuntu
apt-get install zlib1g zlib1g.dev
```
![](assets/【nginx】linux(centos&ubuntu)安装nginx/5.png)
### pcre pcre-devel
Nginx的Rewrite模块和HTTP核心模块会使用到PCRE正则表达式语法。这里需要安装两个安装包pcre和pcre-devel。第一个安装包提供编译版本的库，而第二个提供开发阶段的头文件和编译项目的源代码。
```bash
# centos
yum -y install pcre pcre-devel
# ubuntu
apt-get install libpcre3 libpcre3-dev
```
![](assets/【nginx】linux(centos&ubuntu)安装nginx/6.png)
### openssl openssl-devel
nginx不仅支持 http协议，还支持 https（即在 ssl 协议上传输 http）。如果使用了 https，需要安装 OpenSSL 库。
```bash
# centos
yum -y install openssl openssl-devel
# ubuntu
apt-get install openssl libssl-dev
```
![](assets/【nginx】linux(centos&ubuntu)安装nginx/7.png)
## 编译安装
进入解压后的目录执行`./configure`，之后会生成Makefile文件
默认会安装在 `/usr/local/nginx` 可指定位置 `./configure --prefix=/home/rocyuan/software/nginx`
![](assets/【nginx】linux(centos&ubuntu)安装nginx/8.png)
![](assets/【nginx】linux(centos&ubuntu)安装nginx/9.png)
然后执行`make && make install`会进行编译安装。
![](assets/【nginx】linux(centos&ubuntu)安装nginx/10.png)
## 安装完成
安装完成后进入`/usr/local/nginx/sbin`下会有`nginx可执行文件`
![](assets/【nginx】linux(centos&ubuntu)安装nginx/11.png)
然后访问`localhost`或者本机ip，会显示nginx的欢迎页
![](assets/【nginx】linux(centos&ubuntu)安装nginx/12.png)
![](assets/【nginx】linux(centos&ubuntu)安装nginx/13.png)

