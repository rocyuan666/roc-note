## 手机QQ中打开：

```css
function isQQ() {
  return(navigator.userAgent.toLowerCase().match(/\bqq\b/i) == "qq");
}
```

## 微信中打开：

```css
function isWeixin() {
  return(navigator.userAgent.toLowerCase().match(/MicroMessenger/i) == "micromessenger");
}
```
