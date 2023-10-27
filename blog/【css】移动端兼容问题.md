以下为本人工作，甲方baba测试出的兼容问题，在此记录

## 横竖屏提示兼容问题 

vivoX20 横竖屏提示 输入法键盘按出来，导致屏幕可视区域（landscape，portrait两者都是按照屏幕可视区域宽高进行判断的）高度变小 BUG ；
aspect-ratio 是按照设备中的页面可见区域宽度与高度的比率，小于13/9比率为横屏，大于13/9比率就为竖屏 。

```css
@media all and (orientation : landscape) { //横屏}
@media all and (orientation : portrait){ //竖屏 }
//解决方法：
@media screen and (min-aspect-ratio: 13/9){ } // landscape横屏
@media screen and (max-aspect-ratio: 13/9){ } // portrait竖屏


// 腾讯互娱cp文档中错误，正确改法（横屏提示）：
@media screen and (min-aspect-ratio: 13/9)
{
html,body{position:relative;overflow:hidden;width:100%;height:100%;padding:0;margin:0;}
html::before{content:"";position:fixed;top:0;left:0;height:100%;width:100%;background:#333;z-index:99999;}
html::after{content:"\4E3A\4E86\66F4\597D\7684\4F53\9A8C\FF0C\8BF7\5C06\624B\673A\7AD6\8FC7\6765";text-align:center;font-size:16px;color:#fff;position:absolute;top:50%;left:0;height:30px;width:100%;margin-top:50px;z-index:99999;}
body::before{content:"";position:absolute;zindex:99999;height:200px;width:100px;left:50%;top:50%;margin:-140px 0 0 -50px;color:#fff;backgroundimage:url("//game.gtimg.cn/images/xiawa/cp/a20191107wish/phone.png");background-repeat:no-repeat;background-position:center center;background-size:100px auto;-webkit-transform:rotateZ(-90deg);transform:rotateZ(-90deg);}
}
```

## select选择框文字不居中

iphoneX 中 select选择框文字不兼容居中
利用span模拟选择框

```css
示例：
.serbox .sel-text{
    display: block;
    width: 1.73rem;
    height: .53rem;
    line-height: .53rem;
    color: #fefefe;
    text-align: center;
    text-align-last: center;
    font-size: .26rem;
}
<div class="serbox sp">
	<span id="sel-text0" class="sel-text">选服查看</span>
	<select id="sel0" class="listAll list-select">
		<option value="" selected="selected">选服查看</option>
		<option value="partition">单服</option>
		<option value="all">全服</option>
	</select>
</div>
// select 居中兼容 span模拟
function selJR(id1,id2){
	var show=document.getElementById(id1);
	var sel=document.getElementById(id2);
	sel.onchange=function(){
		var index=sel.selectedIndex; //序号，取当前选中选项的序号
		show.innerText=sel.options[index].text;
	}
}
selJR("sel-text0","sel0");
```

## iphone设备下输入框默认有内阴影

```css
el
{
    -webkit-appearance:none;
}
```
