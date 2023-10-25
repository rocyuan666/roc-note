# 下载
```
wget https://nodejs.org/dist/v16.14.0/node-v16.14.0-linux-x64.tar.xz
```
# 解压
```
tar xzvf node-v16.14.0-linux-x64.tar.xz
```
# 软连接命令
这种方式会存在npm全局安装指令无法使用，建议使用**配置环境变量**
```
ln -s /home/rocyuan/software/node-v16.14.0-linux-x64/bin/npm /usr/local/bin/
ln -s /home/rocyuan/software/node-v16.14.0-linux-x64/bin/node /usr/local/bin/
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1646728320836-80a51b16-091a-47ae-a6b8-41f61a58953a.png#clientId=u302c610d-89a7-4&from=paste&height=180&id=ue2b0f0b1&originHeight=180&originWidth=842&originalType=binary&ratio=1&rotation=0&showTitle=false&size=6337&status=done&style=none&taskId=u15801f82-1b50-4ede-9eaa-1e7dabf19f5&title=&width=842)
# 配置环境变量
修改配置文件（配置PATH环境变量）
```
vi /etc/profile
```
末尾加上`export PATH="$PATH:/home/rocyuan/software/node-v16.14.0-linux-x64/bin/"`
# 更新配置文件
```
source /etc/profile
```
