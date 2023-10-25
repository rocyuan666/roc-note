查看防火墙状态：active（running）防火墙已经被打开；disavtive（dead），防火墙已经被关闭
```bash
systemctl status firewalld.service
```
关闭防火墙：
```bash
systemctl stop firewalld.service
```
永久关闭防火墙：
```bash
systemctl disable firewalld.service
```
