uniapp开发app获取uuid，一般开发会通过chrome先进行调试开发，所以获取uuid方法，我使用了条件编译及promise进行了判断封装。
为什么要条件编译？在chrome中开发调试是h5环境（h5环境获取不到uuid，但后台uuid是必传的情况下）也不会报错（懂的自然懂）。

示例代码（已封装）：

```javascript
/**
 * 获取uuid
 * 使用方法：
 * @return Promise
 */
getUuid() {
  // #ifdef H5
  return new Promise((resolve, reject) => {
    // h5中返回随意的字符（不重要）
    resolve("864771048534920");
  })
  // #endif
  
  // #ifdef APP-PLUS
  return new Promise((resolve, reject) => {
    plus.device.getInfo({
      success: function(res) {
        const uuidList = res.uuid.split(',')
        const UUID = uuidList[0]
        resolve(UUID);
      },
      fail: function(e) {
        reject(e);
      }
    });
  })
  // #endif
},
```
