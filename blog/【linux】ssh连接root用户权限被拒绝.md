# 连接错误
![](assets/【linux】ssh连接root用户权限被拒绝/1.png)
# 解决方案
修改`/etc/ssh/sshd_config`文件
```css
PermitRootLogin yes
```
![](assets/【linux】ssh连接root用户权限被拒绝/2.png)
![](assets/【linux】ssh连接root用户权限被拒绝/3.png)
修改完重启下即可
```css
systemctl restart sshd
```
# 连接成功
![](assets/【linux】ssh连接root用户权限被拒绝/4.png)
