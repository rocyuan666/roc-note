```javascript
// downSuccessStatus为文本提示
// 下载
handleDownload(url) {
  const that = this;
  // #ifndef H5
  that.downSuccessStatus = `下载中，请稍等...`;
  this.downSuccessShow = true;
  uni.downloadFile({
    url: url,
    success: res => {
      if (res.statusCode === 200) {
        uni.saveFile({
          tempFilePath: res.tempFilePath,
          success: function(res) {
            const description = res.savedFilePath;
            that.downSuccessStatus = `下载成功，存储路径为: ${description}`;
          },
          fail: err => {
            that.downSuccessStatus = `存储文件失败`;
          }
        });
      } else {
        that.downSuccessStatus = `下载失败，错误码：${res.statusCode}`;
      }
    },
    fail: err => {
      that.downSuccessStatus = `下载失败`;
    }
  });
  // #endif
  // #ifdef H5
  window.open(url);
  // #endif
		},
```
