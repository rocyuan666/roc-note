多用于游戏页面h5，保存用户游戏生涯等海报
## 使用方法：
```css
<div id="toimg">这个div是需要转为图片的，不能display:none，详见注意事项</div>
<script src="//game.gtimg.cn/images/js/dom2img/1.0.min.js"></script>

<script>
// 生成后的图片会出现在dom元素后面，类名是dom2img-result
dom2img('#toimg')
</script>
```
## 注意事项：

- 用于生成图片的dom元素不能display:none或opacity:0。可以用z-index放到其它元素下面；或者用绝对定位，将其放到某个div容器的可视区之外，然后容器设置overflow:hidden
- 用于生成图片的dom元素的父元素们不能display:none
- 综合1、2，即用于生成图片的dom元素要本身是可见的，且能计算到尺寸值，但不需要出现在视野中
- 生成后的图，会自动追加到用于生成的dom元素后面，类名是dom2img-result，如果不想把图片的样子展示给用户，可将其样式设置为opacity:0
- 某些早期zepto版本内置了一段过时的脚本，会有冲突。如果遇到奇怪的页面问题，请将页面的zepto替换为zepto1.2版本：[https://ossweb-img.qq.com/images/js/zepto/zepto1.2.min.js](https://ossweb-img.qq.com/images/js/zepto/zepto1.2.min.js)
- 图片跨域的缘故，不是所有的图都能合并到最后生成的图中
## 关于横竖屏
由于横竖旋屏过程中无法实时生成图片，在适配上会出现较多的问题，故不建议根据横竖屏的情况生成不同的分享图，建议统一成竖屏或者统一成横屏。
## 生成的图和原dom元素不一样
因为组件是用模拟浏览器渲染的方式，来生成图片，和浏览器自身的渲染方式不完全一致：

1. 生成的图片上的元素层级关系不正确：针对层级关系不正确的元素，手动设置z-index
2. 生成的图缺失原本的dom元素的部分样式，比如没有box-shadow：支持的属性与不支持的CSS属性看[这里](http://html2canvas.hertzen.com/features)
