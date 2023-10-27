`cloudreve.service` 示例

```bash
vim /usr/lib/systemd/system/cloudreve.service
```
```bash
[Unit]
Description=Cloudreve
Documentation=https://docs.cloudreve.org
After=network.target
After=mysqld.service
Wants=network.target

[Service]
WorkingDirectory=/usr/local/cloudreve_3.5.3
ExecStart=/usr/local/cloudreve_3.5.3/cloudreve
Restart=on-abnormal
RestartSec=5s
KillMode=mixed

StandardOutput=null
StandardError=syslog

[Install]
WantedBy=multi-user.target
```

# 新建service

/usr/lib/systemd/system/xxx.service

```bash
[Unit]
# 服务名
Description=service desc
After=network.target
After=mysqld.service
Wants=network.target

[Service]
# 启动脚本
ExecStart=/xxx/xxx/xxx start
# 停止脚本
ExecStop=/xxx/xxx/xxx stop
# 重启脚本
ExecReload=/xxx/xxx/xxx reload
# 发生异常，5s后重启
RestartSec=5s

[Install]
WantedBy=multi-user.target
```

新建完成后刷新配置

```bash
systemctl daemon-reload
```

# systemctl运行命令

```bash
systemctl daemon-reload # 刷新配置

systemctl start xxx.service # 启动服务
systemctl stop xxx.service # 停止服务
systemctl enable xxx.service # 设置开机自启动
systemctl disable xxx.service # 停止开机自启动
systemctl restart xxx.service # 重新启动某服务
systemctl status xxx.service # 查看服务当前状态


systemctl list-units --type=service # 查看所有已启动的服务
systemctl --failed # 查看失败的服务列表
systemctl list-unit-files|grep enabled # 查看成功的服务列表
systemctl reset-failed # 删除所有错误的服务 携带服务名则删除指定的服务
```
