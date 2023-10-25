> **安装环境:Win10 64位**
**软件版本:MySQL 5.7.24 解压版**


## 一、下载

点开下面的链接：
[https://downloads.mysql.com/archives/community/](https://downloads.mysql.com/archives/community/)

![image-20210404200055449.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578042928-a06e796e-775a-4cdf-ab03-3ba8293a17ff.png#clientId=u7035e2a6-af9a-4&from=paste&height=829&id=u540033c2&originHeight=829&originWidth=1798&originalType=binary&ratio=1&rotation=0&showTitle=false&size=137257&status=done&style=none&taskId=u979bad7d-eefc-4e52-a4c7-38a9e06c44e&title=&width=1798)

选择选择和自己**系统位数**相对应的版本点击右边的`Download`，此时会进到另一个页面，同样在接近页面底部的地方找到如下图所示的位置：

![](https://img2018.cnblogs.com/blog/1556823/201812/1556823-20181220194715840-436169502.png#id=C93YM&originHeight=386&originWidth=661&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)

不用理会上面的登录和注册按钮，直接点击`No thanks, just start my download.`就可以下载。

![image-20201109134805641.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578089180-766912cd-45cd-43bb-b925-82a7f3ada60b.png#clientId=u7035e2a6-af9a-4&from=paste&height=44&id=ua6432e4f&originHeight=44&originWidth=249&originalType=binary&ratio=1&rotation=0&showTitle=false&size=2243&status=done&style=none&taskId=u278e8898-ee0b-4e7e-9a84-ef5b8772f14&title=&width=249)

---

## 二、安装(解压)

下载完成后我们得到的是一个压缩包，将其解压，我们就可以得到MySQL 5.7.24的软件本体了(就是一个文件夹)，我们可以把它放在你想安装的位置。

---

![image-20201109134948046.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578112948-02f127ec-ef8f-4a32-8f05-d4956ac8040c.png#clientId=u7035e2a6-af9a-4&from=paste&height=263&id=u62ff404a&originHeight=263&originWidth=603&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20625&status=done&style=none&taskId=u325b4c8f-628c-46a4-8ae5-e329f9594fa&title=&width=603)

## 三、配置

### 1. 添加环境变量

> 环境变量里面有很多选项，这里我们只用到`Path`这个参数。为什么在初始化的开始要添加环境变量呢？
在黑框(即CMD)中输入一个可执行程序的名字，Windows会先在环境变量中的`Path`所指的路径中寻找一遍，如果找到了就直接执行，没找到就在当前工作目录找，如果还没找到，就报错。我们添加环境变量的目的就是能够在任意一个黑框直接调用MySQL中的相关程序而不用总是修改工作目录，大大简化了操作。


右键`此电脑`→`属性`，点击`高级系统设置`

![1556823-20181220220242472-524708778.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578138490-542981c8-0922-4e32-afaf-d305e65435ed.png#clientId=u7035e2a6-af9a-4&from=paste&height=239&id=u10d76c46&originHeight=239&originWidth=275&originalType=binary&ratio=1&rotation=0&showTitle=false&size=11588&status=done&style=none&taskId=ud21fbba9-c351-4c10-8844-513f780da36&title=&width=275)

点击`环境变量`

![1556823-20181220220359609-736422950.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578149132-03b1d140-6c39-455e-a5bd-aabd95efc116.png#clientId=u7035e2a6-af9a-4&from=paste&height=586&id=ue48fb539&originHeight=586&originWidth=472&originalType=binary&ratio=1&rotation=0&showTitle=false&size=22359&status=done&style=none&taskId=ua2b9a6a3-7d60-4da8-89fe-f156411d3e7&title=&width=472)

在`系统变量`中新建MYSQL_HOME

![image-20201109140222488.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578168982-83b4655b-9738-4a56-8402-fad242ab5834.png#clientId=u7035e2a6-af9a-4&from=paste&height=181&id=ued71f5f0&originHeight=181&originWidth=649&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8984&status=done&style=none&taskId=ucd25ea35-d6a5-43b3-80f6-a7dfb9f8edb&title=&width=649)

在`系统变量`中找到并**双击**`Path`

![1556823-20181220220551145-1198958872.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578189348-76fe7470-6afc-4a4d-958c-e798cf7015fa.png#clientId=u7035e2a6-af9a-4&from=paste&height=646&id=uf561b454&originHeight=646&originWidth=607&originalType=binary&ratio=1&rotation=0&showTitle=false&size=31774&status=done&style=none&taskId=u977fd0fe-664b-4c94-bd93-a2a64efde42&title=&width=607)

点击`新建`

![image-20201109135248104.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578209188-5d751125-6b65-426d-9f98-7ee6179af2fe.png#clientId=u7035e2a6-af9a-4&from=paste&height=413&id=u2e44eb4e&originHeight=413&originWidth=510&originalType=binary&ratio=1&rotation=0&showTitle=false&size=25050&status=done&style=none&taskId=u839cc3dc-c2a1-441a-8cd9-86b7f704cdc&title=&width=510)

最后点击确定。

**如何验证是否添加成功？**

右键开始菜单(就是屏幕左下角)，选择`命令提示符(管理员)`，打开黑框，敲入`mysql`，回车。
如果提示`Can't connect to MySQL server on 'localhost'`则证明添加成功；
如果提示`mysql不是内部或外部命令，也不是可运行的程序或批处理文件`则表示添加添加失败，请重新检查步骤并重试。

### 2. 新建配置文件

新建一个文本文件，内容如下：

```properties
[mysql]
default-character-set=utf8

[mysqld]
character-set-server=utf8
default-storage-engine=INNODB
sql_mode=STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION
```

把上面的文本文件另存为，在保存类型里选`所有文件 (*.*)`，文件名叫`my.ini`，存放的路径为MySQL的`根目录`(例如我的是`D:\software\mysql-5.7.24-winx64`,根据自己的MySQL目录位置修改)。

![image-20201109142704951](D:\课程产品\JavaWeb\1. 数据库\1. MySQL基础\资料\imgs\image-20201109142704951.png)

![image-20201109142737584](D:\课程产品\JavaWeb\1. 数据库\1. MySQL基础\资料\imgs\image-20201109142737584.png)

上面代码意思就是配置数据库的默认编码集为utf-8和默认存储引擎为INNODB。

### 3. 初始化MySQL

在刚才的黑框中敲入`mysqld --initialize-insecure`，回车，稍微等待一会，如果出现没有出现报错信息(如下图)则证明data目录初始化没有问题，此时再查看MySQL目录下已经有data目录生成。

```
mysqld --initialize-insecure
```

![image-20201109140955772.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578283405-120a24d8-a1c0-4acd-81f0-61592c4dcd4f.png#clientId=u7035e2a6-af9a-4&from=paste&height=197&id=ufb27df82&originHeight=197&originWidth=491&originalType=binary&ratio=1&rotation=0&showTitle=false&size=5719&status=done&style=none&taskId=u35d95054-10f3-44e2-ada9-a4a3b13542c&title=&width=491)

tips：如果出现如下错误

![image-20201109135848054.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578297595-79e10ca1-8a1d-4438-9ac7-9ede3bfa7077.png#clientId=u7035e2a6-af9a-4&from=paste&height=95&id=u5533909e&originHeight=95&originWidth=959&originalType=binary&ratio=1&rotation=0&showTitle=false&size=6184&status=done&style=none&taskId=u3a6ad1d6-25c6-4ff8-ba99-330ea3936e9&title=&width=959)

是由于权限不足导致的，去`C:\Windows\System32` 下以管理员方式运行 cmd.exe

![image-20201109140423691.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578315175-9b100a89-969a-4d3b-b782-5ffc85e92c1e.png#clientId=u7035e2a6-af9a-4&from=paste&height=188&id=ud3566dda&originHeight=188&originWidth=459&originalType=binary&ratio=1&rotation=0&showTitle=false&size=19235&status=done&style=none&taskId=udb9f4e18-3bf2-4ba1-94fc-3aac6eff182&title=&width=459)

![image-20201109140001186.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578336564-b03ade56-c29c-494d-85a4-a31f0400b031.png#clientId=u7035e2a6-af9a-4&from=paste&height=147&id=u3dfcd196&originHeight=147&originWidth=730&originalType=binary&ratio=1&rotation=0&showTitle=false&size=5212&status=done&style=none&taskId=u593edd9f-678d-4415-b4df-83eb72eff4e&title=&width=730)

### 4. 注册MySQL服务

在黑框里敲入`mysqld -install`，回车。

```
mysqld -install
```

![image-20201109141325810.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578356076-0a6e4579-fcca-491c-93f3-d11d93ec6c21.png#clientId=u7035e2a6-af9a-4&from=paste&height=93&id=ubb810135&originHeight=93&originWidth=441&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1946&status=done&style=none&taskId=u7fd99c53-264e-47ae-b08f-4b2508027ad&title=&width=441)

现在你的计算机上已经安装好了MySQL服务了。

MySQL服务器

### 5. 启动MySQL服务

在黑框里敲入`net start mysql`，回车。

```java
net start mysql  // 启动mysql服务
    
net stop mysql  // 停止mysql服务
```

![1556823-20181221093036851-1317238155.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578378456-278fb96f-07e1-4154-ad30-78dbf47ee011.png#clientId=u7035e2a6-af9a-4&from=paste&height=68&id=u97a90aca&originHeight=68&originWidth=297&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1849&status=done&style=none&taskId=ub8e393d3-dd38-4edc-8184-496ae00d4aa&title=&width=297)

### 6. 修改默认账户密码

在黑框里敲入`mysqladmin -u root password 1234`，这里的`1234`就是指默认管理员(即root账户)的密码，可以自行修改成你喜欢的。

```
mysqladmin -u root password 1234
```

![1556823-20181221093251250-819416425.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578393895-687ca064-7060-48ca-a9a5-6f304f427c4a.png#clientId=u7035e2a6-af9a-4&from=paste&height=75&id=uf7c576ba&originHeight=75&originWidth=726&originalType=binary&ratio=1&rotation=0&showTitle=false&size=3709&status=done&style=none&taskId=u63c23cbf-50ff-40dc-94c7-d974ae7e286&title=&width=726)

**至此，MySQL 5.7 解压版安装完毕！**

---

## 四、登录MySQL

右键开始菜单，选择`命令提示符`，打开黑框。
在黑框中输入，`mysql -uroot -p1234`，回车，出现下图且左下角为`mysql>`，则登录成功。

```
mysql -uroot -p1234
```

![1556823-20181220222422178-61579658.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578419608-682c75e1-1062-44f5-a9ff-05f8b4c30af4.png#clientId=u7035e2a6-af9a-4&from=paste&height=323&id=ub641c313&originHeight=323&originWidth=640&originalType=binary&ratio=1&rotation=0&showTitle=false&size=12234&status=done&style=none&taskId=u57e92721-5250-4744-9fcf-224f33efe9f&title=&width=640)

**到这里你就可以开始你的MySQL之旅了！**

退出mysql：

```
exit
quit
```

登陆参数：

```
mysql -u用户名 -p密码 -h要连接的mysql服务器的ip地址(默认127.0.0.1) -P端口号(默认3306)
```

---

## 五、卸载MySQL

如果你想卸载MySQL，也很简单。

右键开始菜单，选择`命令提示符(管理员)`，打开黑框。

1. 敲入`net stop mysql`，回车。

```
net stop mysql
```

![1556823-20181220222924783-57600848.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578436849-a8542c90-e782-430c-9665-96ecb3a1cba9.png#clientId=u7035e2a6-af9a-4&from=paste&height=192&id=u8317d6f7&originHeight=192&originWidth=366&originalType=binary&ratio=1&rotation=0&showTitle=false&size=5267&status=done&style=none&taskId=uc0a5d369-d288-4bf3-8069-ffd2ed64d05&title=&width=366)

2. 再敲入`mysqld -remove mysql`，回车。

```
mysqld -remove mysql
```

![1556823-20181220223025128-587235464.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1652578453653-3d2a8289-be95-496f-8845-42f41663e91a.png#clientId=u7035e2a6-af9a-4&from=paste&height=99&id=ub1e2a016&originHeight=99&originWidth=336&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1973&status=done&style=none&taskId=uf44192c7-5f6a-4713-b2ef-ae9a142f69b&title=&width=336)

3. 最后删除MySQL目录及相关的环境变量。

**至此，MySQL卸载完成！**
