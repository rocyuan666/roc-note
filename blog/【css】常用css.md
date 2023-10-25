```css
/* 字间距： */
p{
	letter-spacing: 1px;
}

/* 单行省略号 */
.sl{
  overflow:hidden;
  white-space:nowrap;
  text-overflow:ellipsis;
}

/* 多行省略号 */
.sl2 {
  display: -webkit-box !important;
  overflow: hidden;
  text-overflow: ellipsis;
  word-break: break-all;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical !important;
}

/* 画三角形 */
.box{
	content: '';
  position: absolute;
  border: 10px solid transparent;
  border-bottom-color: pink;
}

/* 文字不被选中 */
body {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* css“>”符号: */
.more:after {
  border-color: #666;
  position: absolute;
  right: ;(具体位置具体定)
  top: ;(具体位置具体定)
  display: block;
  content: '';
  width: .6em;
  height: .6em;
  border-left: .04rem solid #06c1ae; 
  border-bottom: .04rem solid #06c1ae;
  transform: translateY(-50%) scaleY(.7) rotateZ(-135deg);
  -webkit-transform: translateY(-50%) scaleY(.7) rotateZ(-135deg);
  -moz-transform: translateY(-50%) scaleY(.7) rotateZ(-135deg);
  -ms-transform: translateY(-50%) scaleY(.7) rotateZ(-135deg); 
}

/* css“<”符号: */
.more:after {
  border-color: #666;
  position: absolute;
  right: ;(具体位置具体定)
  top: ;(具体位置具体定)
  display: block;
  content: '';
  width: .6em;
  height: .6em;
  border-right: .04rem solid #06c1ae; (和上面相比就改了这)
  border-top: .04rem solid #06c1ae;(和上面相比就改了这)
  transform: translateY(-50%) scaleY(.7) rotateZ(-135deg);
  -webkit-transform: translateY(-50%) scaleY(.7) rotateZ(-135deg);
  -moz-transform: translateY(-50%) scaleY(.7) rotateZ(-135deg);
  -ms-transform: translateY(-50%) scaleY(.7) rotateZ(-135deg); 
}

/* 字体： */
@font-face{
  font-family: '字体名称随便起'; 
  src: url('../font/字体名称.eot');
  src:url('../font/字体名称.woff') format('woff'),
    url('../font/字体名称.ttf') format('truetype'),
    url('../font/字体名称.svg') format('svg');
}

/* 移动端改变滚动条样式 */
.list {  
  overflow: hidden;  
  overflow-y: auto;  
}  
.list::-webkit-scrollbar-track-piece {  
  background-color: rgba(0, 0, 0, 0);  
  border-left: 1px solid rgba(0, 0, 0, 0);  
}  
.list::-webkit-scrollbar {  
  width: 5px;  
  height: 13px;  
  -webkit-border-radius: 5px;  
  -moz-border-radius: 5px;  
  border-radius: 5px;  
}  
.list::-webkit-scrollbar-thumb {  
  background-color: rgba(0, 0, 0, 0.5);  
  background-clip: padding-box;  
  -webkit-border-radius: 5px;  
  -moz-border-radius: 5px;  
  border-radius: 5px;  
  min-height: 28px;  
}  
.list::-webkit-scrollbar-thumb:hover {  
  background-color: rgba(0, 0, 0, 0.5);  
  -webkit-border-radius: 5px;  
  -moz-border-radius: 5px;  
  border-radius: 5px;  
}  

/* 整个滚动条的样式 */
::-webkit-scrollbar {
  width: 10px;
  height: 10px;
}
::-webkit-scrollbar-track-piece {
  background-color: rgba(0, 0, 0, 0.2);
  -webkit-border-radius: 6px;
}
::-webkit-scrollbar-thumb:vertical {
  height: 5px;
  background-color: rgba(125, 125, 125, 0.7);
  -webkit-border-radius: 6px;
}
::-webkit-scrollbar-thumb:horizontal {
  width: 5px;
  background-color: rgba(125, 125, 125, 0.7);
  -webkit-border-radius: 6px;
}
/*
倾斜
-webkit-transform: skew(-3deg,-1deg)

table隔行换色 
table tr:nth-child(odd) 奇数
table tr:nth-child(even) 偶数

table 合并边框 
border-collapse:collapse;
*/

/* 表格中图片垂直居中 */
img{
  vertical-align:middle
}

/* TG横竖屏兼容问题 */
@media screen and (min-aspect-ratio: 13/9){ } // landscape  横屏
@media screen and (max-aspect-ratio: 13/9){ } // portrait   竖屏

/* 文本两端对齐 */
text-align: justify;

/* 文字英文数字也换行 */
word-break: break-all;

/*
所有表单的placeholder 默认颜色
IE9及以下版本不支持input的placeholder属性，需要用JS来做兼容。
*/
input::-webkit-input-placeholder{
  color:red;
}
input::-moz-placeholder{   /* Mozilla Firefox 19+ */
  color:red;
}　　
input:-moz-placeholder{    /* Mozilla Firefox 4 to 18 */
  color:red;
}
input:-ms-input-placeholder{  /* Internet Explorer 10-1*/
	color:red;
}

/* 去除激活input的默认边框, 三种方法都能实现 */
input{
  outline: none;
  outline: medium;
  outline: 0;
} 

/* textarea禁止拖动 */
textarea{
	resize: none;
}

```
