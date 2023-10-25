# 安卓
## 隐私政策服务协议
        根据工业和信息化部关于开展APP侵害用户权益专项整治要求，应用启动运行时需弹出隐私政策协议，说明应用采集用户数据，这里将详细介绍如何配置弹出“服务协议和隐私政策”提示框。
![1650848275(1).png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1650848278443-a8848d1a-598f-4493-9078-2bb49d739fac.png#clientId=ubbf2711b-62d3-4&from=paste&height=427&id=n6x6U&originHeight=589&originWidth=319&originalType=binary&ratio=1&rotation=0&showTitle=false&size=327441&status=done&style=none&taskId=u4d5569d1-2691-4d61-9e28-1b7241ee351&title=&width=231)
服务协议内容参考：
[app-服务协议-示例](https://www.yuque.com/rocyuan/blog/ypv7i6?view=doc_embed)
隐私政策内容参考：
[app-隐私政策-示例](https://www.yuque.com/rocyuan/blog/yd4auh?view=doc_embed)
### 添加

1. 开启“使用原生隐私政策提示框”

![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1650848378571-491d7890-b7cc-43b3-a703-2f68b9cc910e.png#clientId=ubbf2711b-62d3-4&from=paste&height=573&id=u5b234a1c&originHeight=573&originWidth=725&originalType=binary&ratio=1&rotation=0&showTitle=false&size=56751&status=done&style=none&taskId=u0f6c276b-3697-494a-8e5d-8b103730e31&title=&width=725)

2. 项目根目录添加`androidPrivacy.json`文件

message中的链接地址需要更换
```javascript
{
    "version" : "1",
    "prompt" : "template",
    "title" : "服务协议和隐私政策",
    "message" : "　　请你务必审慎阅读、充分理解“服务协议”和“隐私政策”各条款，包括但不限于：为了更好的向你提供服务，我们需要收集你的设备标识、操作日志等信息用于分析、优化应用性能。<br/>　　你可阅读<a href=\"https://www.xxx.com/fuwuxieyi.html\">《服务协议》</a>和<a href=\"https://www.xxx.com/yinsizhengce.html\">《隐私政策》</a>了解详细信息。如果你同意，请点击下面按钮开始接受我们的服务。",
    "buttonAccept" : "同意并接受",
    "buttonRefuse" : "暂不同意",
    "second" : {
        "title" : "确认提示",
        "message" : "　　进入应用前，你需先同意<a href=\"https://www.xxx.com/fuwuxieyi.html\">《服务协议》</a>和<a href=\"https://www.xxx.com/yinsizhengce.html\">《隐私政策》</a>，否则将退出应用。",
        "buttonAccept" : "同意并继续",
        "buttonRefuse" : "退出应用"
    },
    "styles" : {
        "backgroundColor" : "#f8f8fb",
        "borderRadius" : "5px",
        "title" : {
            "color" : "#333333"
        },
        "buttonAccept" : {
            "color" : "#333333"
        },
        "buttonRefuse" : {
            "color" : "#333333"
        }
    }
}

```
## 应用权限说明
上架应用市场需要说明应用每项权限的用处，可能每个平台存在差异，上架华为应用市场时官方会提供填写说明权限的文档模板。
### 应用权限
可以在manifest.json文件中安卓权限配置中勾选，也可在源码试图中找到。
安卓权限有很多，可自行查询意思，如下：
android.permission.ACCESS_COARSE_LOCATION      网络定位的权限（比较粗略）
android.permission.ACCESS_FINE_LOCATION      GPS定位的权限（比较精准）
android.permission.CAMERA      使用相机的权限
android.permission.INTERNET      使用网络的权限
android.permission.WRITE_EXTERNAL_STORAGE      写入储存卡的权限
android.permission.READ_EXTERNAL_STORAGE      读取储存卡的权限
......
uniapp云端打包后会自动添加权限：[https://ask.dcloud.net.cn/article/36982](https://ask.dcloud.net.cn/article/36982)，可在app上架前检查是否有多余的app权限，进行简化。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1650849332234-37b59bc3-2270-40cc-baf8-662ca4afea8c.png#clientId=ubbf2711b-62d3-4&from=paste&height=808&id=u25b203d9&originHeight=808&originWidth=1114&originalType=binary&ratio=1&rotation=0&showTitle=false&size=97728&status=done&style=none&taskId=u92220957-a854-427f-8ee8-d53df409620&title=&width=1114)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1650849403721-e7377d56-38ca-4c71-b1db-0477c6f4091b.png#clientId=ubbf2711b-62d3-4&from=paste&height=810&id=u2f21a393&originHeight=810&originWidth=1327&originalType=binary&ratio=1&rotation=0&showTitle=false&size=99983&status=done&style=none&taskId=u0d19bda1-03b0-4136-bb69-afe2dcbad92&title=&width=1327)
## 注销账号
上架应用市场要求app有注销账号功能，使用户可以自行注销自己的账号，从而在服务器删除自己的信息。
## 版权信息
需要添加版权信息
![7239430146e373fe140897fdbfd5d85.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1651020189277-43e91424-ccb1-4b18-98b4-d05eb46b5cb2.png#clientId=u9fac1f02-5226-4&from=paste&height=476&id=u9ce64726&originHeight=476&originWidth=271&originalType=binary&ratio=1&rotation=0&showTitle=false&size=33781&status=done&style=none&taskId=u441c62d2-bdac-4cd0-bd37-ce76ba21f94&title=&width=271)
## 资质证书
开发app的功能不同，所需要的资质证书也就不同，但是软著必须得有；比如app内有发布资讯新闻功能，还得提供新闻信息服务资质许可证...，可根据自己app功能查询需要的证书。
## 应用完整度
app功能不完善的情况下，不要抱着，先上架后期更新的心理去上架，会被打回来的审核不过；未完善的功能可以先隐藏掉。
![1650850228(1).png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1650850230675-618ecf46-87dc-4265-beeb-58e21333e84e.png#clientId=u088fc540-8173-4&from=paste&height=408&id=u9e55cd69&originHeight=408&originWidth=1057&originalType=binary&ratio=1&rotation=0&showTitle=false&size=338857&status=done&style=none&taskId=u8504589b-abe3-4992-89ed-4de7d4a529d&title=&width=1057)
