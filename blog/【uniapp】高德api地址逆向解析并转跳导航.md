web解析同理
申请两个key：
Android平台：用于打包填写maps模块key
Web服务：用于逆向解析key（代码里要用，建议提取到项目config.js文件）

```javascript
// 处理 定位地址 导航 cfg为导入的项目config对象
handleNavigation(address) {
  const key = cfg.webGaoDeKey;
  // 逆向解析
  uni.request({
    url: `https://restapi.amap.com/v3/geocode/geo?address=${address}&key=${key}`,
    success(res) {
      if(res.data.status == 1){
        const [longitude, latitude] = res.data.geocodes[0].location.split(",")
        console.log(longitude, "经度")
        console.log(latitude, "维度")
        // 打开地图导航
        uni.openLocation({
          longitude: Number(longitude),
          latitude: Number(latitude),
          name: address,
          address: address,
          success(res) {
            console.log(res)
          },
          fail(err){
            console.log(err)
          }
        })
      }else{
        uni.showToast({
          icon: "none",
          mask: true,
          title: res.data.info
        })
      }
    }
  })
},
```
