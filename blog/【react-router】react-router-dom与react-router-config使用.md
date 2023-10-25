## react-router-dom使用
HashRouter：路由的类型，哈希模式
BrowserRouter：路由的类型，HTML5 history模式
NavLink：路由按钮默认转成a标签，选中的路由对应的a标签带有active的class名；Link不带active的class名。
Route：匹配路由显示对应的组件
Redirect：重定向
Switch：匹配到对应路由时不会向下匹配
……更多api及属性查看react-router官网
[https://reactrouter.com/web/guides/quick-start](https://reactrouter.com/web/guides/quick-start)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840399819-e82ca71e-3526-413b-b482-c938cdb6c384.png#clientId=ua9f979b2-3581-4&from=paste&id=u5f839e04&originHeight=555&originWidth=400&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u05a9468b-efcf-459e-bc05-67f5f6fa98a&title=)
这样写路由在项目中路由不利于管理（以上还只是简单的单层路由，还没有路由业务），于是我们会用 react-router-config统一管理路由。
## react-router-config使用
用react-router-config提供的renderRoutes方法渲染显示的组件，renderRouter接收一个参数，这个参数可定义路由及重定向等…
更多使用方式参考
[https://www.npmjs.com/package/react-router-config](https://www.npmjs.com/package/react-router-config)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840399498-8f84503f-a7e6-4305-9497-819ed0fb06a0.png#clientId=ua9f979b2-3581-4&from=paste&id=u84234694&originHeight=418&originWidth=491&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u7de96b20-d736-46aa-b0b1-4b29fccb499&title=)
![](https://cdn.nlark.com/yuque/0/2021/png/2779910/1628840399506-c62d4a8b-93db-4347-91cd-6ebc85709dac.png#clientId=ua9f979b2-3581-4&from=paste&id=ua9928495&originHeight=523&originWidth=429&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ua85e5c53-1f38-416d-b772-f9a12c0d1c2&title=)
## 结果演示
![](https://cdn.nlark.com/yuque/0/2021/gif/2779910/1628840400155-d92b9b18-4085-42eb-861c-6b161e717a2e.gif#clientId=ua9f979b2-3581-4&from=paste&id=u14bf30b1&originHeight=250&originWidth=594&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ub553a576-a3d0-440e-adea-35cc347ed52&title=)
