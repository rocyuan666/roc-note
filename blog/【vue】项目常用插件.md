## 图片懒加载
```css
npm install vue-lazyload --save

import VueLazyLoad from 'vue-lazyload'
 
//注册时可传入对象：
 Vue.use(VueLazyLoad,{
    //未加载出来的占位图
    loading: require('./xxxpng')
 })
//使用懒加载：img :src='' 更改为 img v-lazy=''
```
## 顶部进度条
```css
npm install nprogress --save
import NProgress from 'nprogress'
// 导入进度条样式
import 'nprogress/nprogress.css'
//请求,响应拦截配置
NProgress.start() 显示进度条
NProgress.done() 隐藏进度条
```
## px单位转换
```css
npm install postcss-px-to-viewport --save-dev

//个人不常用
//修改 postcss.config.js

module.exports = {
  plugins: {
    autoprefixer: {},
    "postcss-px-to-viewport": {
      viewportWidth: 375,  //视窗宽度
      viewportHeight: 667,  //视窗高度
      unitPrecision: 5,  //指定`px`转换为视窗单位值的小数位数
      viewportUnit: 'vw',  //指定需要转成的视窗单位，建议vw
      // selectorBlackLict: ['',''],  //指定不需要转换的类   出问题！！！
      exclude: [/正则/], 正则匹配的不做转换  出问题！！！
      minPixelCalue: 1,  //小于1px不转换
      mediaQuery: false  //允许在媒体查询中转换`px`
    }
  }
}
```
