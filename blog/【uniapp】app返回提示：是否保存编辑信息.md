表单内容过多时，用户编辑表单，编辑到一半，返回时询问保存编辑信息，保存后下次进来自动填写保存的表单内容。
```javascript
onBackPress(e) {
  const that = this;
  if (e.from == "backbutton") {
    if (!that.isEdit) {
      uni.showModal({
        title: "提示",
        content: "是否保留此次编辑？",
        success(res) {
          if (res.confirm) {
            // 保存编辑（执行创建数据缓存的方法）
            that.createDataStorageSync()
            uni.navigateBack()
          } else {
            uni.navigateBack()
          }
        }
      })
    } else {
      uni.navigateBack()
    }
    return true; //阻止默认返回行为
  }
},
```
