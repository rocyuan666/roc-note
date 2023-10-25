**移动端加：**
```javascript
// 不是移动设备里跳转到PC地址
if(!/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|OperaMini/i.tesst(navigator.userAgent)) {
	window.location = "/cp/a11111212xx/index.htm";
}
```
**PC中加：**
```javascript
//是移动端跳转到移动地址
if(/Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|OperaMini/i.test(navigator.userAgent) ) {
	window.location = "/cp/a11111212xxm/index.htm";
}
```
