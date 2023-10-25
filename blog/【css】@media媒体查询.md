使用@media媒体查询响应式兼容判断
@media(条件){……}
```css
彩色屏幕和最小宽度1000下
@media only screen and (min-width:1000px){#wrap{}}

/* mobile adaptation start */
@media (device-height:480px) and (-webkit-min-device-pixel-ratio:2){/* 兼容iphone4/4s */
.topbox{padding-top:50px;}
}
@media (device-height:568px) and (-webkit-min-device-pixel-ratio:2){/* 兼容iphone5 */
.topbox{padding-top:70px;}
}
@media (device-height:667px) and (-webkit-min-device-pixel-ratio:2){/* 兼容iphone6 */
.topbox{padding-top:100px;}
}
@media (device-height:736px) and (-webkit-min-device-pixel-ratio:2){/* 兼容iphone6 Plus */
.topbox{padding-top:130px;}
}


/* bootstrap 媒体查询 - 视口划分 */
html {
  font-size: 10px;
}
@media (max-width: 767px) {
  html {
    font-size: 8.5px;
  }
}
@media (min-width: 768px) {
  html {
    font-size: 9px;
  }
}
@media (min-width: 992px) {
  html {
    font-size: 9.5px;
  }
}
@media (min-width: 1200px) {
  html {
    font-size: 10px;
  }
}

```
