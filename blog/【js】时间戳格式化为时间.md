```javascript
function formatDate(date, fmt) {
  if (/(y+)/.test(fmt)) {
    fmt = fmt.replace(RegExp.$1, (date.getFullYear() + '').substr(4 - RegExp.$1.length));
  }
  let o = {
    'M+': date.getMonth() + 1,
    'd+': date.getDate(),
    'h+': date.getHours(),
    'm+': date.getMinutes(),
    's+': date.getSeconds()
  };
  for (let k in o) {
    if (new RegExp(`(${k})`).test(fmt)) {
      let str = o[k] + '';
      fmt = fmt.replace(RegExp.$1, (RegExp.$1.length === 1) ? str : padLeftZero(str));
    }
  }
  return fmt;
};
function padLeftZero (str) {
  return ('00' + str).substr(str.length);
};
```

**参数说明：**
formatDate(date, fmt)
date: 时间对象
fmt: 对应时间戳返回的时间格式，如下：
（”yyyy-MM-dd hh:mm:ss”）返回（2000-12-21 12:12:12）
使用示例：
const dateNum = 1232654521122 // 瞎写的时间戳
const date = new Date(dateNum)
console.log(formatDate(date, ‘yyyy/MM/dd hh:mm:sss’))
打印： dateNum时间戳对应的时间（当然是错的，只演示格式）：
2000/12/21 12:12:12
