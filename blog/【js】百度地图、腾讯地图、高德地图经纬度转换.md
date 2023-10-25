# 常见坐标系标准
**WGS-84（地球坐标系）**：是目前广泛使用的GPS全球卫星定位系统使用的坐标系；谷歌地图、GPS模块使用。
**GCJ-02（火星坐标系）**：是由中国国家测绘局制定的地理坐标系统，是由WGS-84加密后得到的坐标系；高德地图、腾讯地图使用。
**BD-09（百度坐标系）**：是百度坐标系，在GCJ-02坐标系基础上再次加密；百度地图使用。
# 腾讯、高德转百度
```javascript
// 将腾讯、高德地图经纬度转换为百度地图经纬度
function qqMapTransBMap(lng, lat) {
  let x_pi = (3.14159265358979324 * 3000.0) / 180.0;
  let x = lng;
  let y = lat;
  let z = Math.sqrt(x * x + y * y) + 0.00002 * Math.sin(y * x_pi);
  let theta = Math.atan2(y, x) + 0.000003 * Math.cos(x * x_pi);
  let lngs = z * Math.cos(theta) + 0.0065;
  let lats = z * Math.sin(theta) + 0.006;
  return {
    lng: lngs,
    lat: lats,
  };
}
```
# 百度转腾讯、高德
```javascript
// 将百度地图经纬度转换为腾讯、高德地图经纬度
function bMapTransQQMap(lng, lat) {
  let x_pi = (3.14159265358979324 * 3000.0) / 180.0;
  let x = lng - 0.0065;
  let y = lat - 0.006;
  let z = Math.sqrt(x * x + y * y) - 0.00002 * Math.sin(y * x_pi);
  let theta = Math.atan2(y, x) - 0.000003 * Math.cos(x * x_pi);
  let lngs = z * Math.cos(theta);
  let lats = z * Math.sin(theta);
  return {
    lng: lngs,
    lat: lats,
  };
}
```
