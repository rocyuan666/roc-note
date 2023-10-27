## 下载

百度网盘下载：  
链接：[https://pan.baidu.com/s/1l3OWoOEcLkjxGLPBpbJWOg?pwd=8zgv ](https://pan.baidu.com/s/1l3OWoOEcLkjxGLPBpbJWOg?pwd=8zgv )  
提取码：`8zgv`

## 配置

1. 下载 `MySql.Data.dll` 文件（压缩包内有）  
下载地址:   
https://www.dll-files.com/mysql.data.dll.html  
https://downloads.mysql.com/archives/c-net/  
2. 将 `MySql.Data.dll` 复制到 `CodeSmith` 的 `bin` 文件夹下
3. 修改 `CodeSmith` 安装目录下的 `TemplateEditor.exe.config`， 在最后结尾的 `</configuration>` 之前加入以下行：

```xml
<system.data>
    <DbProviderFactories>
        <add name="MySQL Data Provider" invariant="MySql.Data.MySqlClient" description=".Net Framework Data Provider for MySQL" type="MySql.Data.MySqlClient.MySqlClientFactory, MySql.Data, Version=8.0.16.0, Culture=neutral, PublicKeyToken=c5687fc88969c44d" />
    </DbProviderFactories>
</system.data>
```

4. 确认下载的 `MySql.Data.dll` 版本号和上述字符串中的`Version`（版本）一致, 保存关闭文件, 重启 `CodeSmith`  
**第 3 步 中配置版本号与压缩包内 `MySql.Data.dll` 文件版本一致，可直接使用！**

5. 在 `Schama Explorer` 面板中新增数据库，`provider Type` 选择 `MySQLSchamaProvider`, 连接字符串如下:

```
server=172.0.0.1;User ID=root;Password=root;database=DB_NAME;
```

6. `Test` 测试成功，`Add` 保存

7. 解决mysql获取表、字段注释为空问题需要将压缩包内 `SchemaExplorer.MySQLSchemaProvider.dll` 替换到 `/CodeSmith/v8.5/SchemaProviders/SchemaExplorer.MySQLSchemaProvider.dll`

8. 编写模板，在 `Properties` 面板中选择数据库表，进行代码生成。

## 示例代码

示例模板代码：  
[https://github.com/rocyuan666/codesmith_template](https://github.com/rocyuan666/codesmith_template)
