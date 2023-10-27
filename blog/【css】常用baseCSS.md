## PC端：

```css
body,dl,dd,ul,ol,h1,h2,h3,h4,h5,h6,p,form,header,section,article,footer{margin:0;}
body,button,input,select,textarea{font:12px/1.5 tahoma,'\5FAE\8F6F\96C5\9ED1',sans-serif}
h1,h2,h3,h4,h5,h6{font-size:100%}
em,b{font-style:normal}
a{text-decoration:none} 
a:hover{text-decoration:underline}
img{border:0} 
body{padding-top:42px} 
button,input,select,textarea{font-size:100%;outline:none}
table{border-collapse:collapse;border-spacing:0}
td,th,ul,ol{padding:0}
```

## 移动端：

```css
/* 移动端常用reset.css (文字版本) */
/* reset */
html,body,div,p,ul,li,dl,dt,dd,em,i,span,a,img,input,h1,h2,h3,h4,h5 {margin:0;padding:0}
a,img,input {border:none;}
body{font: 14px/1.75 -apple-system, "Helvetica Neue", Helvetica, Arial, sans-serif;}
table{border-collapse:collapse;border-spacing:0}
a {text-decoration:none;}
ul,li{list-style: none}



/* 移动端常用reset.css (无文字版本) */
/* reset */
html,body,div,p,ul,li,dl,dt,dd,em,i,span,a,img,input,h1,h2,h3,h4,h5 {margin:0;padding:0}
a,img,input {border:none;}
body{font: 14px/1.75  -apple-system, "Helvetica Neue", Helvetica, Arial, sans-serif;-webkit-tap-highlight-color: rgba(0,0,0,0);}
table{border-collapse:collapse;border-spacing:0}
a {text-decoration:none;}
ul,li{list-style: none}
a, img {-webkit-touch-callout: none; /* 禁止长按链接与图片弹出菜单 */}
html, body {
    -webkit-user-select: none;   /* 禁止选中文本（如无文本选中需求，此为必选项） */
    user-select: none;
}
```

## PC常用（TX互娱cp）：

```css
/* reset */
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,form,fieldset,input,textarea,p,blockquote,th,td{margin:0;padding:0;}
table{border-collapse:collapse;border-spacing:0;}
address,caption,cite,code,dfn,em,strong,th,var{font-weight:normal;font-style:normal;}
ol,ul{list-style:none;}
h1,h2,h3,h4,h5,h6{font-weight:normal;font-size:100%;}
q:before,q:after{content:'';}
fieldset,img,abbr,acronym{border:0;}
/* basic */
.c:before,.c:after{content:"";display:table;}
.c:after{clear:both;}
.c{zoom:1;}
body {font-family:'\5FAE\8F6F\96C5\9ED1';font-size:12px;background-color: #191e32;}
a {text-decoration:none;overflow:hidden;}
a:hover {text-decoration:none;}
.wrap {min-width:1200px;overflow: hidden;}
.container {width:1200px;margin:0 auto;}
.hide {display:block;width:0;height:0;overflow:hidden;}
.mt{margin-top: 90px;}
.pr {position:relative;}
.pa {position:absolute;}
.db{display:block;text-indent:-999em;}
.sp{background: url(../images/sp.png) no-repeat;background-position: 9999px 9999px;}
.cont{left: 0;top: 50%;margin-top: -298px;}
.line-bg{top: 60px;left: -360px;z-index: -1;-webkit-animation:  fadeIn 2s;animation: fadeIn 2s;}
.min-title{position: relative;width: 411px;height: 60px;background-position: -312px 0;margin-bottom: 16px;}
.min-title h2{position: absolute;left: 95px;top:-4px;font-size:38px;font-weight: bold;color:#ff4c36;}
.main img{display: block;}
```

## 畅游cp：

```css
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, font, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td {
	margin: 0;
	padding: 0;
	border: 0;
	outline: 0;
	font-size: 100%;
	background: transparent;
}
table {
	border-collapse:collapse;
	border-spacing:0;
}
fieldset, img {	border:0; }
address, caption, cite, code, dfn, em, strong, th, var {
	font-style:normal;
	font-weight:normal;
}
ol, ul { list-style:none; }
caption, th { text-align:left; }
h1, h2, h3, h4, h5, h6 {
	font-size:100%;
	font-weight:normal;
}
:focus { outline: 0;}
a{ text-decoration:none;}
a:hover img{ border:none;}

/*清除浮动*/
.clearfix:after {
	content: ".";
	display: block;
	height: 0;
	clear: both;
	visibility: hidden;
}
.clearfix {display: inline-block;}
/* Hides from IE-mac \*/
* html .clearfix { height: 1%;}
.clearfix {display: block;}
/* End hide from IE-mac */

/*png css hack for ie6*/
*html img.png{
    _background-image: expression(this.runtimeStyle.backgroundImage = "none",this.runtimeStyle.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='" + this.src + "', sizingMethod='image')",this.src = "http://i0.itc.cn/20101019/848_0a785a7b_1118_4825_85dc_e8696988c94b_0.gif");
}
/*Extra CSS File For Change on All The Websites*/
@import url(http://www1.changyou.com/styles/extra.css);
```
