```bash
server
{
	listen 80;
  server_name 192.168.0.147;
  index index.php index.html index.htm default.php default.htm default.html;
  root /www/wwwroot/192.168.0.147;

	# 目录模式配置
  location /
  {
    autoindex on; # 开启目录模式
    autoindex_exact_size off; # 关闭准确大小（显示KB\MB\GB）
    autoindex_localtime on; # 显示服务器本地时间
  }
}

```
