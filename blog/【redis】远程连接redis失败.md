连接另一台服务器redis服务失败
修改配置文件 `redis.conf`

```bash
bind 0.0.0.0
# 127.0.0.1 表示只允许本地访问,无法远程连接
# 0.0.0.0   表示任何ip都可以访问

protected-mode no
# yes 保护模式，只允许本地链接
# no  保护模式关闭
```

修改完重启redis
