![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1667878944868-57bb3311-1c52-4708-b6c7-5644ad769b36.png#averageHue=%23fbfbfb&clientId=u57c90163-3102-4&from=paste&height=481&id=u42ba164d&originHeight=481&originWidth=1849&originalType=binary&ratio=1&rotation=0&showTitle=false&size=33712&status=done&style=none&taskId=u07f4e76a-db04-4dbf-ac5a-f760ee66942&title=&width=1849)
```javascript
(function (window) {
  var userAgent = navigator.userAgent;
  var isIE = userAgent.indexOf("compatible") > -1 && userAgent.indexOf("MSIE") > -1;
  var isIE11 = userAgent.indexOf("Trident") > -1 && userAgent.indexOf("rv:11.0") > -1;
  var compatibilityMode = window.navigator.userAgent.indexOf("compatible") != -1;
  if (isIE || isIE11 || compatibilityMode) {
    var str = "抱歉！您浏览的页面无法正常显示";
    var str2 = "推荐使用Chrome，Firefox，Edge浏览器，如果您使用的是360、搜狗、QQ等双核浏览器，";
    var str1 = "请切换到极速模式访问";
    var str3 = "./img/jiantou.png";
    var str4 = "./img/logo.png";
    document.write(
      "<div><div style='width:900px;margin:0 auto;font-family:Microsoft YaHei'>" +
        "<p style='padding-top:100px;margin:0;text-align:center;margin-bottom:40px;color:#999;font-size:30px;'>" +
        str +
        "<br/></p><p style='color:#999;font-size:20px;margin-left:50px;'>" +
        str2 +
        "</br>" +
        str1 +
        "</p>" +
        "<div style='text-align:center;'></div>" +
        "</div></div>"
    );
  }
})(window);
```
