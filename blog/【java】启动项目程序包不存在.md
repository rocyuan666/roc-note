# 程序包org.apache.poi.ss.usermodel
## 问题
启动项目报错`java程序包org.apache.poi.ss.usermodel`不存在。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1660996099300-9b53ff23-1702-41f9-a844-936aaa289334.png#clientId=ufa8c3eb9-4ee9-4&from=paste&height=371&id=ub525d6fb&originHeight=371&originWidth=794&originalType=binary&ratio=1&rotation=0&showTitle=false&size=47647&status=done&style=none&taskId=ub87cc6e3-e8f6-44bb-ba05-5f67b5c377c&title=&width=794)
## 解决方案
在项目根目录运行`mvn idea:idea`更新不完整依赖
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1660996118813-eeb91773-07f1-49e0-8e9d-dda870cd78bd.png#clientId=ufa8c3eb9-4ee9-4&from=paste&height=388&id=u1cf23a8a&originHeight=388&originWidth=834&originalType=binary&ratio=1&rotation=0&showTitle=false&size=25185&status=done&style=none&taskId=u090cfddd-3048-4142-8303-520d3c47988&title=&width=834)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1660996126222-e7c21fcb-0539-4db3-bdc1-c0f957b5e4e8.png#clientId=ufa8c3eb9-4ee9-4&from=paste&height=358&id=u1cde303a&originHeight=358&originWidth=757&originalType=binary&ratio=1&rotation=0&showTitle=false&size=45109&status=done&style=none&taskId=u6e928a41-c1f7-4747-8601-c16c417e4a3&title=&width=757)
如果依旧报错，清除缓存重启
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1660996152315-ba941821-8987-4a64-9c30-fc900c898945.png#clientId=ufa8c3eb9-4ee9-4&from=paste&height=452&id=u0fd6eb94&originHeight=452&originWidth=633&originalType=binary&ratio=1&rotation=0&showTitle=false&size=67485&status=done&style=none&taskId=u1251db4c-bb84-40e9-be7f-c7cb9b87bca&title=&width=633)

