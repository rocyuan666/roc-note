## 简介：

Gitea 的首要目标是创建一个极易安装，运行非常快速，安装和使用体验良好的自建 Git 服务。项目采用 Go 作为后端语言，只要生成一个可执行程序即可。
它是跨平台的，支持 Linux、macOS 和 Windows 以及各种架构，除了 x86，amd64，还包括 ARM 和 PowerPC。

## **前提：**

安装git与mysql

## 安装gitea:

最新版本下载地址：[https://dl.gitea.io/gitea](https://dl.gitea.io/gitea)

```css
wget -O gitea https://dl.gitea.io/gitea/1.6.0/gitea-1.6.0-linux-amd64
chmod +x gitea
nohup ./gitea web &
```

## 配置域名

在nginx中设置反向代理：

```css
server
  {
      listen 80;
      server_name git.roc.com;
      location / {
        proxy_pass http://localhost:3000/;
      }
  }
```

![](assets/【linux】centos7部署私有git并用域名访问/1.png)
