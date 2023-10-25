```javascript
//屏幕适应 
(function (win, doc) {
  if (!win.addEventListener) return;
  var html = document.documentElement;
  function setFont() {
    var html = document.documentElement;
    var k = 640;
    html.style.fontSize = html.clientWidth / k * 100 + "px";
  }
  setFont();
  setTimeout(function () {
    setFont();
  }, 300);
  doc.addEventListener('DOMContentLoaded', setFont, false);
  win.addEventListener('resize', setFont, false);
  win.addEventListener('load', setFont, false);
})(window, document);
```
k= 宽度
若设计稿按照750设计，k=750；设计稿640，k=640… ；
使用时，ps中量取的 px/100 即是rem
如：18px 则 .18rem
