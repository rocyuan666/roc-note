# 下载
官网下载：[https://www.telerik.com/fiddler/fiddler-classic](https://www.telerik.com/fiddler/fiddler-classic)
# 配置fiddler
一.由于fiddler只默认抓取HTTP的请求，若想抓取HTTPS的请求，则需要设置HTTPS的各项值：
第一步：在fiddler菜单项选择Tools -> Options -> HTTPS
第二步：勾选【Decrypt HTTPS traffic 】【Ignore server certificate errors】，下拉框默认：【from all processes】 即可
第三步：点击右边的【Actions】，选择【Trust Root Certificate】点击，弹出窗点击【Yes】按钮即可。
第四步：点击【OK】保存
![](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588253792-5d389351-250a-4f56-bd14-5388e6c20ffd.png#clientId=u4d3b396b-7bd4-4&from=paste&id=tgwmT&originHeight=346&originWidth=942&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u57aadaae-e5ea-4340-a3d9-fcc93c0d0a7&title=)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588274934-916a8200-de7c-43f1-a2c7-b30289645a7f.png#clientId=u4d3b396b-7bd4-4&from=paste&id=SVeGA&originHeight=504&originWidth=1769&originalType=url&ratio=1&rotation=0&showTitle=false&size=694066&status=done&style=none&taskId=ua74beca2-4295-44d2-9dca-713a8e1a0ba&title=)
二.设置fiddler connections的值，允许fiddler远程连接
第一步：在fiddler菜单项选择Tools  ->  Options -> connections
第二步：勾选【|Allow remote computers to connect】
第三步：点击【ok】
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588327136-9f7170cd-fb48-4501-8bba-ee914dda3589.png#clientId=u4d3b396b-7bd4-4&from=paste&id=u2fc53077&originHeight=726&originWidth=1305&originalType=url&ratio=1&rotation=0&showTitle=false&size=509793&status=done&style=none&taskId=u82c28546-4e85-44fb-96c4-add89f06d88&title=)
##重要事情说三遍
更改完设置一定要重启fiddler！！！
更改完设置一定要重启fiddler！！！
更改完设置一定要重启fiddler！！！
三.在手机上进行相应的设置，为手机抓包做准备
1.查看自己本机的IP
方法一：电脑——左下角点击Windows图标——输入cmd，打开cmd面板，输入：ipconfig ，查看本机IP地址
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588352663-9d555883-2078-4b81-8268-f7c989e06736.png#clientId=u4d3b396b-7bd4-4&from=paste&id=uaec9c73a&originHeight=497&originWidth=552&originalType=url&ratio=1&rotation=0&showTitle=false&size=28892&status=done&style=none&taskId=u7589b092-9fee-492e-9a95-b64ccbd52d6&title=)
方法二：在fiddler主界面，将鼠标移到【online】上面，就可以查看本地的IP地址了，如果你的fiddler没有显示【online】，可以通过【fiddler菜单——View——Show Toolbar】将【Show Toolbar】勾选中，就会显示【Online】信息了。
![](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588372095-e0a5d448-2960-4181-8a7e-05df688f8a64.png#clientId=u4d3b396b-7bd4-4&from=paste&id=uc359783c&originHeight=130&originWidth=942&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u7971152c-6993-421e-9885-c0ddcfa9950&title=)
2.手机安装证书。（ios设置和Android设置基本一样）
前提条件：
手机和电脑要处于同一网络条件下（可以理解为：使用同一个WiFi）
fiddler的默认端口是：8888，不需要进行修改，使用默认的就可以。
一个手机可以安装多个证书，但是每安装的一个证书里面都设置有IP地址，所以：安装的证书和电脑IP是一一对应的，当前的这个证书只能针对某一台电脑使用，更换电脑后，该证书将不能使用，只能重新安装与更换的电脑的IP相同的证书才能使用。
第一步：手机下载证书。打开手机的浏览器，输入：【IP:8888】下载证书。
例如：浏览器输入【[http://192.168.xxx.xxx:8888](http://192.168.xxx.xxx:8888)】或者【192.168.xxx.xxx:8888】（这个地方的IP就是你电脑的IP）
![](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588393409-c537114e-8a05-4641-9182-6475f5896acf.png#clientId=u4d3b396b-7bd4-4&from=paste&id=ud713e005&originHeight=844&originWidth=854&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u0661db54-5c05-46a6-8d9e-07b53122276&title=)
第二步：安装证书.
 有的手机可以直接点击已下载的文件进行安装，有的手机则不行。
如果不能直接安装证书，我们可以通过以下方法来安装证书。
1.Android：安装证书。由于安装系统众多，设置的方法不尽相同，下面几个方法以供参考。
方法一：手机——设置——搜索【证书】二字——选择：安装证书或者证书管理：点击安装证书，在你的众多文件里面去选择刚刚下载的fiddler的证书，点击安装
（注：选择安装的文件后，需要输入手机的锁屏密码。Android一定要有锁屏密码才能安装证书）
![](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588430859-5cce694d-6ed6-4b41-9dfc-6bfe0909436c.png#clientId=u4d3b396b-7bd4-4&from=paste&id=u45aa6d76&originHeight=750&originWidth=759&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u32b7a07c-c2e5-44c2-91e4-ea5dd4f9ace&title=)
方法二：在浏览器里面，直接打开已经下载的文件，安装即可，安装步骤是：先输入手机锁屏密码——后到上图为证书命名界面。
证书安装好后，查看已信任证书：具体位置在【安全——更多安全设置——加密和凭据——受信任的凭据】
![](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588445877-1ec10267-728d-419b-9a4a-62f1fb160980.png#clientId=u4d3b396b-7bd4-4&from=paste&id=u7fc4ef2a&originHeight=742&originWidth=356&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uac32e2ba-2065-4c24-90f7-d859db592f7&title=)
2.ios安装证书：直接点击已下载的文件安装即可，安装文件成功后，需要在【设置——通用——关于本机——证书信任设置】开启证书信任。
第三步：为手机设置代理.（ios和安卓差不多）
设置——无线网络（WLAN）——WLAN——长按已连接的WiFi 去修改网络——在高级选项里面——选择【手动代理】——出现以下界面，按图所示操作即可。
（或者长按通知栏WiFi按钮进入WiFi界面）
（有的机型需要先添加网络才能对网络进行修改，这个看个人手机情况）
![](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588464827-8e3afccb-1964-4f91-998a-35e1360d3e93.png#clientId=u4d3b396b-7bd4-4&from=paste&id=ubbb0da7d&originHeight=743&originWidth=355&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u2fcd1ec2-66ae-4db9-a7c3-b99e1583444&title=)
第四步：访问手机浏览器或者任一应用就可以在fiddler里面查看到抓取的请求了
最后查看已经抓取到的https的请求：
![](https://cdn.nlark.com/yuque/0/2022/png/2779910/1666588476525-2a66e850-a836-4433-b69d-78ef3a0806ab.png#clientId=u4d3b396b-7bd4-4&from=paste&id=ua2833686&originHeight=507&originWidth=942&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ue196753c-6b79-4c06-af29-c68f9bbb9d3&title=)

【转载】[https://blog.csdn.net/Vandalism520/article/details/124930187](https://blog.csdn.net/Vandalism520/article/details/124930187)
