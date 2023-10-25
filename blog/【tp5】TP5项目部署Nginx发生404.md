tp5项目在Apache中运行一切正常，但部署在nginx环境中，页面打不开提示404报错。
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825878350-2c05c122-6a92-411a-93bd-0104bec019d0.png#clientId=u927d6409-2969-4&from=paste&id=u85348c3c&originHeight=610&originWidth=918&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u5d02c464-565f-40c0-a9d2-c7d3745e2c6&title=)
解决方案：
宝塔网站 -> 设置 -> 配置文件
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628825879135-e987216e-c138-4689-a669-940ce81c69a9.png#clientId=u927d6409-2969-4&from=paste&id=u782534a3&originHeight=598&originWidth=741&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ue6cc0675-2673-4ceb-80d5-d98817c3f21&title=)
```javascript
# nginx tp项目404
location / {
  index index.html index.htm index.php;
  #autoindex on;
  if (!-e $request_filename) {
    rewrite ^(.*)$ /index.php?s=/$1 last;
    break;
  }
}
```
搞定！
