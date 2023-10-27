在脚手架项目里使用到了sass，我们npm install时node-sass出现的问题总是最多的。

## 分析安装步骤

其实node-sass它是依赖binding.node这么一个文件的；
首先npm下载node-sass，然后会检测全局和本地中是否有binding.node文件，如果有即跳过安装，没有则从github下载该二进制文件并将其缓存到全局，假如binding.node下载失败，则尝试本地编译出该文件，而本地编译过程就需要python环境，一般它会提示需要python27环境（如果以上问题解决就不会出现这一步）。

## 原因1-下载node-sass，源慢（国外的源）

可使用nrm管理npm源，切换到taobao源（首先要安装nrm）

`nrm use taobao`
或者直接将npm设置成taobao源：
`npm config set registry https://registry.npm.taobao.org`

## 原因2-binding.node下载过慢或无法访问

binding.node下载默认是github地址，国内访问较慢有时候还无法访问。我们也可以将其改成国内的地址：
`npm config set sass_binary_site=https://npm.taobao.org/mirrors/node-sass`

## 原因3-node版本与node-sass版本不兼容

参考官方：[https://github.com/sass/node-sass](https://github.com/sass/node-sass)

| **NodeJS** | **Supported node-sass version** | **Node Module** |
| --- | --- | --- |
| Node 15 | 5.0+ | 88 |
| Node 14 | 4.14+ | 83 |
| Node 13 | 4.13+, <5.0 | 79 |
| Node 12 | 4.12+ | 72 |
| Node 11 | 4.10+, <5.0 | 67 |
| Node 10 | 4.9+ | 64 |
| Node 8 | 4.5.3+, <5.0 | 57 |
| Node <8 | <5.0 | <57 |

## 原因4-提示没有安装python、build失败等

如果上面的都可以解决这一步实际上是本地编译需要的python环境等，按照提示装python环境即可，一般是python27版本。
