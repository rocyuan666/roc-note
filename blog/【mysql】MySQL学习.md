# 数据库备份

```bash
mysqldump -u用户名 -p密码 --databases 数据库1 数据库2 > xxx.sql
```

# 字段数据类型

 可以分为三类：数值、日期、字符串

| 分类 | 数据类型 | 大小 | 描述 |
| --- | --- | --- | --- |
| 数值类型 | tinyint | 1 byte | 小整数值 |
|  | smallint | 2 bytes | 大整数值 |
|  | mediumint | 3 bytes | 大整数值 |
|  | int或integer | 4 bytes | 大整数值age int |
|  | bigint | 8 bytes | 极大整数值 |
|  | float | 4 bytes | 单精度浮点数值 |
|  | double | 8 bytes | 双精度浮点数值score double(总长度, 保留小数位)如：0-100, 保留两位小数score double(5, 2) |
|  | decimal |  | 小数值 |
| 日期和时间类型 | date | 3 | 日期值 |
|  | time | 3 | 时间值或持续时间 |
|  | year | 1 | 年份值 |
|  | datetime | 8 | 混合日期和时间值 |
|  | timestamp | 4 | 混合日期和时间值，时间戳 |
| 字符串类型 | char | 0-255 bytes | 定长字符串name char(10) 最长10个字符储存空间，没有存够10个字符也是占10个字符空间。储存性能高，浪费空间 |
|  | varchar | 0-65535 bytes | 变长字符串name varchar(10)最长10个字符储存空间，占了几个字符就是几个字符储存空间。储存性能低，节省空间 |
|  | tinyblob | 0-255 bytes | 不超过 255 个字符的二进制字符串 |
|  | tinytext | 0-255 bytes | 短文本字符串 |
|  | blob | 0-65 535 bytes | 二进制形式的长文本数据 |
|  | text | 0-65 535 bytes | 长文本数据 |
|  | mediumblob | 0-16 777 215 bytes | 二进制形式的中等长度文本数据 |
|  | mediumtext | 0-16 777 215 bytes | 中等长度文本数据 |
|  | longblob | 0-4 294 967 295 bytes | 二进制形式的极大文本数据 |
|  | longtext | 0-4 294 967 295 bytes | 极大文本数据 |

# DDL(Data Definition Language)数据定义语言

用来定义数据库对象：数据库，表，字段等，DDL简单理解就是对数据库，表进行增（Create）删（Delete）改（Update）查（Retrieve）等

## 操作数据库

```sql
-- 查看所有数据库
SHOW DATABASES;

-- 新建数据库
CREATE DATABASE 数据库名;
CREATE DATABASE IF NOT EXISTS 数据库名;

-- 删除数据库
DROP DATABASE 数据库名;
DROP DATABASE IF EXISTS 数据库名;

-- 使用数据库
USE 数据库名;

-- 查看当前使用的数据库
SELECT DATABASE();
```

## 操作表

```sql
-- 查看所有表
SHOW TABLES;

-- 查询表结构
DESC 表名;

-- 新建表
CREATE TABLE 表名(
  字段名1 字段1数据类型,
  字段名2 字段2数据类型,
  字段名3 字段3数据类型,
  ...
  字段名n 字段n数据类型
);
CREATE TABLE IF NOT EXISTS 表名(
  字段名1 字段1数据类型,
  字段名2 字段2数据类型,
  字段名3 字段3数据类型,
  ...
  字段名n 字段n数据类型
);

-- 删除表
DROP TABLE 表名;
DROP TABLE IF EXISTS 表名;

-- 修改表
-- 修改表名
ALTER TABLE 表名 RENAME TO 新表名;
-- 添加字段
ALTER TABLE 表名 ADD 字段 字段数据类型;
-- 修改字段数据类型
ALTER TABLE 表名 	MODIFY 字段名 新的字段数据类型;
-- 修改字段及字段数据类型
ALTER TABLE 表名 CHANGE 字段名 新字段 新字段数据类型;
-- 删除字段
ALTER TABLE 表名 DROP 字段名;

```

# DML(Data Manipulation Language)数据操作语言

用来对数据库中表的数据进行增删改，DML简单理解就对表中数据进行增（insert）删（delete）改（update）

```sql
-- 添加
-- 添加指定字段的值，批量添加则在value后跟多组值
INSERT INTO 表名 (字段1, 字段2...) VALUES (值1, 值2...), (值1, 值2...)...;
-- 添加全部字段的值，也可以在表名后写全部字段值进行添加，，批量添加则在value后跟多组值
INSERT INTO 表名 VALUES (值1, 值2, 值3...);

-- 修改
-- 根据 WHERE条件 修改，不指定 WHERE 则修改表中全部数据！！！
-- 修改多个字段SET后多组用“,”隔开
UPDATE 表名 SET 字段1=值1, 字段2=值2... WHERE id=1;

-- 删除
-- 根据 WHERE条件 删除，不指定 WHERE 则删除表中全部数据！！！
DELETE FROM 表名 WHERE id=1;

```

# DQL(Data Query Language)数据查询语言

用来查询数据库中表的记录
查询的完整写法：

```sql
SELECT
字段列表
FROM
表名
WHERE
条件列表
GROUP BY
分组字段
HAVING
分组后条件
ORDER BY
排序字段
LIMIT
分页限定
```

## 基础查询

```sql
-- 查询所有字段的数据
SELECT * FROM 表名;

-- 查询指定字段的数据
SELECT 字段1,字段2... FROM 表名;

-- 查询的数据去重
SELECT DISTINCT 字段 FROM 表名;

-- 起别名 AS, AS可以省略
SELECT 字段1 AS 别名1, 字段2 AS 别名2 FROM 表名;
SELECT 字段1 别名1, 字段2 别名2 FROM 表名;
```

## 条件查询

### 语法

```sql
-- 语法
SELECT 字段列表 FROM 表名 WHERE 条件列表
```

### 条件

| **符号** | **功能** |
| --- | --- |
| = | 等于 |
| > | 大于 |
| >= | 大于等于 |
| < | 小于 |
| <= | 小于等于 |
| <>或!= | 不等于 |
| BETWEEN...AND... | 在某个范围内（都包含） |
| IN(...) | 多选一 |
| LIKE 占位符 | 模糊查询 _单个任意字符 %多个任意字符 []指定范围([a-z])或者集合[abcd] |
| IS NULL | 是NULL |
| IS NOT NULL | 不是NULL |
| AND或&& | 并且 |
| OR或&#124;&#124; | 或者 |
| NOT或! | 不 |

## 排序查询

```sql
-- 语法 排序方式分为 ASC 升序  DESC降序
-- 如果有多个排序条件，第一个数据一样时，才会根据第二个进行排序...
SELECT 字段列表 FROM 表名 ORDER BY 字段1 [排序方式1], 字段2 [排序方式2];
SELECT * FROM  表名 ORDER BY age ASC, name DESC;
```

## 聚合函数

聚合函数就是将一列数据（某个字段的数据）进行计算（纵向计算）。

### 语法

```sql
-- 注意！！！所有聚合函数都不会计算null值
SELECT 聚合函数(字段名) from 表名;
```

### 分类

| **函数名** | **功能** |
| --- | --- |
| count(字段) | 统计数量（一般选择没有null的列，建议写*） |
| max(字段) | 最大值 |
| min(字段) | 最小值 |
| sum(字段) | 求和 |
| avg(字段) | 平均值 |

## 分组查询

注意：分组之后，查询的字段为聚合函数和分组字段，查询其他字段无任何意义！！！

```sql
SELECT 字段列表 FROM 表名 [WHERE 分组前条件查询] GROUP BY 分组字段名 [HAVING 分组后条件过滤];
```

where与having区别：

- 执行实际不同：where是在分组前执行，不满足where条件的不进行分组；having是分组后执行，对分组后的数据进行过滤。
- 可以判断的条件不同：where不能对聚合函数进行判断，而having可以。

## 分页查询

注意：索引从0开始！！！

```sql
SELECT 字段列表 FROM 数据库 LIMIT 起始索引, 查的条数;
```

起始索引 = (当前页码 - 1) * 查的条数

# DCL(Data Control Language)数据控制语言

 用来定义数据库的访问权限和安全级别，及创建用户 DML简单理解就是对数据库进行权限控制。比如我让某一个数据库表只能让某一个用户进行操作等

# 约束

## 分类

| 类型 | 关键字 | 描述 |
| --- | --- | --- |
| 非空约束 | NOT NULL | 所有列中数据不允许有null值 |
| 唯一约束 | UNIQUE | 所有列中数据不能相同 |
| 主键约束 | PRIMARY KEY | 主键是数据的唯一标识，要求唯一且非空。 |
| 检查约束 | CHECK | 保证某一列数据在某个范围.注意：mysql不支持检查约束，只能通过代码进行限制。 |
| 默认约束 | DEFAULT | 添加默认值 |
| 外键约束 | FOREIGN KEY | 外键用来让两张表的数据建立连接 |


## 示例

```sql
-- 部门表 （自动增长示例）
CREATE TABLE tb_dept(
id int primary key auto_increment,
dep_name varchar(20),
addr varchar(20)
);

-- =================== 外键约束语法 =====================
-- 创建表时添加外键约束语法
CREATE TABLE 表名(
  列名 数据类型,
  …
  [CONSTRAINT] [外键名称] FOREIGN KEY(外键列名) REFERENCES 主表(主表列名)
);
-- 建完表后添加外键约束
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES 主表名称(主表列名称);
-- 删除外键约束
ALTER TABLE 表名 DROP FOREIGN KEY 外键名称;
-- =================== 外键约束语法 =====================

-- 员工表 （添加外链示例）
CREATE TABLE tb_emp(
id int primary key auto_increment,
name varchar(20),
age int,
dep_id int,
-- 添加外键 dep_id,关联 dept 表的id主键
CONSTRAINT fk_emp_dept FOREIGN KEY(dep_id) REFERENCES tb_dept(id)
);
```

# 多表查询

```sql
-- 从表名1和表名2中查询所有字段（会把每种交集情况的数据全部查询出来，一般需要去除无效数据）
SELECT * FROM 表名1, 表名2;

-- 去除无效数据
SELECT * FROM 表名1, 表名2 WHERE 表名1.字段(一般是外键字段) = 表名2.字段(被外键连接的字段)
```

## 内连接查询

相当于查询两表交集数据。

```sql
-- 隐式内连接
SELECT 字段列表 FROM 表名1, 表名2,... WHERE 条件;

-- 显示内连接 INNER 可省略
SELECT 字段列表 FROM 表名1 [INNER] JOIN 表2 ON 条件;
```

# 外连接查询

分为左外连接，右外连接
左外连接：查询左边表所有数据和交集部分数据
右外连接：查询右边表所有数据和交集部分数据

```sql
-- 左外连接
SELECT 字段列表 FROM 表名1 LEFT JOIN 表名2 ON 条件;

-- 右外连接
SELECT 字段列表 FROM 表名1 RIGHT JOIN 表名2 ON 条件;
```

# 子查询（嵌套查询）

```sql
-- 示例如下:
SELECT 字段名 FROM 表名 WHERE xxx字段 > (SELECT xxx字段 FROM 表名 WHERE 条件);

SELECT * FROM emp WHERE dep_id IN (SELECT id from dept WHERE name = '市场部' OR name = '财务部');
```

# 事务

数据库事务是一个操作序列，包含了一组数据库命令，要么同时成功，要么同时失败；一组命令中其中一个出错之前执行的命令都可以被回滚。

## 语法

```sql
-- 开启事务
START TRANSACTION;
-- 或者
BEGIN;

-- 提交事务
COMMIT;

-- 回滚事务
ROLLBACK;
```

mysql中事务是自动提交的，不添加事务执行sql语句，语句执行完会自动提交事务。
通过`SELECT @@autocommit;`查询提交方式，`SET @@autocommit = 1 || 0;` 修改（1自动提交，0手动提交）。

## 事务四大特征（ACID）

- 原子性（Atomicity）: 事务是不可分割的最小操作单位，要么同时成功，要么同时失败
- 一致性（Consistency） :事务完成时，必须使所有的数据都保持一致状态
- 隔离性（Isolation） :多个事务之间，操作的可见性
- 持久性（Durability） :事务一旦提交或回滚，它对数据库中的数据的改变就是永久的 
 
# 连接池 - Druid（德鲁伊）

- 导入jar包
- 定义配置文件
- 加载配置文件
- 获取数据库连接池
- 获取连接
- 
```properties
driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/dbname?useSSL=false&useServerPrepStmts=true
username=root
password=root
# 初始化连接数量
initialSize=5
# 最大连接数
maxActive=10
# 最大等待时间
maxWait=3000
```

```java
public class DruidDemo {
    public static void main(String[] args) throws Exception {
        //  1 导入连接池的jar包 druid
        //  2 定义配置文件
        //  3 加载配置文件
        Properties prop = new Properties();
        prop.load(new FileInputStream("02-jdbc/src/druid.properties"));
        //  4 获取数据库连接池对象
        DataSource dataSource = DruidDataSourceFactory.createDataSource(prop);
        //  5 获取连接
        Connection conn = dataSource.getConnection();
        //  获取到连接对象以后的操作与之前一样...
        Statement stmt = conn.createStatement();
        String sql = "UPDATE users set name='rocyuan' where id=1";
        int code = stmt.executeUpdate(sql);
        System.out.println(code);
    }
}
```
