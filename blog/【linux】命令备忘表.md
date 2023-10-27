## 1) 系统

| uname | 显示 Linux 系统信息 |
| --- | --- |
| uname -r | 显示内核版本信息 |
| uptime | 显示系统运行了多长时间，包括平均负载 |
| hostname | 显示系统主机名 |
| hostname -i | 显示系统的 IP 地址 |
| last reboot | 显示系统重启历史 |
| date | 显示当前系统日期和时间 |
| timedatectl | 查询和更改系统时钟 |
| cal | 显示当前日历月和日 |
| w | 显示系统中当前登录的用户 |
| whoami | 显示您的登录身份 |
| finger username | 显示有关用户的信息 |

## 2) 硬件

| dmesg | 显示启动消息 |
| --- | --- |
| cat /proc/cpuinfo | 显示有关 CPU 的更多信息，例如型号、型号名称、内核、供应商 ID |
| cat /proc/meminfo | 显示有关硬件内存的更多信息，例如 Total 和 Free memory |
| lshw | 显示有关系统硬件配置的信息 |
| lsblk | 显示块设备相关信息 |
| free -m | 显示系统中的空闲和已用内存（-m 标志表示内存以 MB 为单位） |
| lspci -tv | 以树状图显示 PCI 设备 |
| lsusb -tv | 以树状图显示 USB 设备 |
| dmidecode | 显示来自 BIOS 的硬件信息 |
| hdparm -i /dev/xda | 显示有关磁盘数据的信息 |
| hdparm -tT /dev/xda <:code> | 在设备 xda 上进行读取速度测试 |
| badblocks -s /dev/xda | 测试磁盘上不可读的块 |

## 3) 用户

| id | 显示活动用户的详细信息，例如 uid、gid 和组 |
| --- | --- |
| last | 显示系统中的最后一次登录 |
| who | 显示谁登录到系统 |
| groupadd "admin" | 添加组“管理员” |
| adduser "rocyuan" | 添加用户 rocyuan |
| userdel "rocyuan" | 删除用户 rocyuan |
| usermod | 用于更改/修改用户信息 |

## 4) 文件命令

| ls -al | 列出文件 - 常规和隐藏文件及其权限。 |
| --- | --- |
| pwd | 显示当前目录文件路径 |
| mkdir 'directory_name' | 创建一个新目录 |
| rm file_name | 删除文件 |
| rm -f filename | 强制删除文件 |
| rm -r directory_name | 递归删除目录 |
| rm -rf directory_name | 以递归方式强制删除目录 |
| cp file1 file2 | 将file1的内容复制到file2 |
| cp -r dir1 dir2 | 递归地将 dir1 复制到 dir2。dir2 如果不存在则创建 |
| mv file1 file2 | 将文件1重命名为文件2 |
| ln -s /path/to/file_name   link_name | 创建指向 file_name 的符号链接 |
| touch file_name | 创建一个新文件 |
| cat > file_name | 将标准输入放入文件 |
| more file_name | 输出文件的内容 |
| head file_name | 显示文件的前 10 行 |
| tail file_name | 显示文件的最后 10 行 |
| gpg -c file_name | 加密文件 |
| gpg file_name.gpg | 解密文件 |
| wc | 打印文件中的字节数、字数和行数 |
| xargs | 从标准输入执行命令 |

## 5) 进程相关

| ps | 显示当前活动的进程 |
| --- | --- |
| ps aux &#124; grep 'telnet' | 搜索进程 'telnet' 的 id |
| pmap | 显示进程的内存映射 |
| top |  显示所有正在运行的进程 |
| kill pid | 使用给定的 pid 终止进程 |
| killall proc | 杀死/终止所有名为 proc 的进程 |
| pkill process-name | 使用名称向进程发送信号 |
| bg | 在后台恢复暂停的作业 |
| fg | 将暂停的作业置于前台 |
| fg n | 工作 n 到前台 |
| lsof | 列出进程打开的文件 |
| renice 19 PID | 使进程以非常低的优先级运行 |
| pgrep firefox | 查找 Firefox 进程 ID |
| pstree | 在树模型中可视化流程 |

## 6) 文件权限

| chmod octal filename | 将文件的文件权限更改为八进制 |
| --- | --- |
| chmod 777 /data/test.c | 将 rwx 权限设置为所有者、组和所有人（有权访问服务器的其他所有人） |
| chmod 755 /data/test.c | 将 rwx 设置为所有者，将 r_x 设置为组和所有人 |
| chmod 766 /data/test.c | 为所有者设置 rwx，为组和每个人设置 rw |
| chown owner user-file | 更改文件的所有权 |
| chown owner-user:owner-group file_name | 更改文件的所有者和组所有者 |
| chown owner-user:owner-group directory | 更改目录的所有者和组所有者 |

## 7) 网络

| ip addr show | 显示 IP 地址和所有网络接口 |
| --- | --- |
| ip address add 192.168.0.1/24 dev eth0 | 将 IP 地址 192.168.0.1 分配给接口 eth0 |
| ifconfig | 显示所有网络接口的 IP 地址 |
| ping host | ping 命令发送 ICMP 回显请求以建立与服务器/PC 的连接 |
| whois domain | 检索有关域名的更多信息 |
| dig domain | 检索有关域的 DNS 信息 |
| dig -x host | 对域执行反向查找 |
| host google.com | 对域名执行 IP 查找 |
| hostname -i | 显示本地 IP 地址 |
| wget file_name | 从在线资源下载文件 |
| netstat -pnltu | 显示所有活动的监听端口 |

## 8) 压缩/存档

| tar -cf home.tar home<:code> | 从文件 'home' 创建名为 'home.tar' 的存档文件 |
| --- | --- |
| tar -xf files.tar | 提取存档文件“files.tar” |
| tar -zcvf home.tar.gz source-folder | 从源文件夹创建 gzipped tar 归档文件 |
| gzip file | 压缩扩展名为 .gz 的文件 |

## 9) 安装软件包

| rpm -i pkg_name.rpm | 安装一个 rpm 包 |
| --- | --- |
| rpm -e pkg_name | 删除一个 rpm 包 |
| dnf install pkg_name | 使用 dnf 实用程序安装软件包 |

## 10) 安装源（编译）

| ./configure | 检查您的系统是否有构建程序所需的软件。它将构建包含有效构建项目所需的说明的 Makefile |
| --- | --- |
| make | 它读取 Makefile 以编译具有所需操作的程序。该过程可能需要一些时间，具体取决于您的系统和程序的大小 |
| make install | 该命令在编译后将二进制文件安装在默认/修改路径中 |

## 11) 搜索

| grep 'pattern' files | 在文件中搜索给定的模式 |
| --- | --- |
| grep -r pattern dir | 递归搜索给定目录中的模式 |
| locate file | 查找文件的所有实例 |
| find /home -name "index" | 在 /home 文件夹中查找以 'index' 开头的文件名 |
| find /home -size +10000k | 在主文件夹中查找大于 10000k 的文件 |

## 12) 登录

| ssh user@host | 以用户身份安全连接到主机 |
| --- | --- |
| ssh -p port_number user@host | 使用指定端口安全连接到主机 |
| ssh host | 通过 SSH 默认端口 22 安全连接到系统 |
| telnet host | 通过 telnet 默认端口 23 连接到主机 |

## 13) 文件传输

| scp file1.txt server2/tmp | 安全地将 file1.txt 复制到 /tmp 目录中的 server2 |
| --- | --- |
| rsync -a /home/apps  /backup/ | 将 /home/apps 目录中的内容与 /backup 目录同步 |

## 14) 磁盘使用情况

| df -h | 显示已安装系统上的可用空间 |
| --- | --- |
| df -i | 显示文件系统上的空闲 inode |
| fdisk -l | 显示磁盘分区、大小和类型 |
| du -sh | 以人类可读的格式显示当前目录中的磁盘使用情况 |
| findmnt | 显示所有文件系统的目标挂载点 |
| mount device-path mount-point | 挂载设备 |

## 15)目录遍历

| cd .. | 在目录树结构中上移一级 |
| --- | --- |
| cd | 将目录更改为 $HOME 目录 |
| cd /test | 将目录更改为 /test 目录 |


