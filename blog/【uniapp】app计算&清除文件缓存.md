注意不是Storage缓存是app资源文件缓存
```vue
<template>
	<view>
		<view class="cont-wrap">
			<view class="listItem" @click="clern">
				<view class="itemLeft">
					<text>清除缓存</text>
				</view>
				<view class="itemRight">
					<text class="rtext">{{fileSizeString}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				fileSizeString: ""
			}
		},
		onLoad() {
			this.formatSize();
		},
		methods: {
			// 获取缓存
			formatSize() {
				let that = this;
				// #ifdef APP-PLUS
				plus.cache.calculate(function(size) {
					let sizeCache = parseInt(size);
					if (sizeCache == 0) {
						that.fileSizeString = "0B";
					} else if (sizeCache < 1024) {
						that.fileSizeString = sizeCache + "B";
					} else if (sizeCache < 1048576) {
						that.fileSizeString = (sizeCache / 1024).toFixed(2) + "KB";
					} else if (sizeCache < 1073741824) {
						that.fileSizeString = (sizeCache / 1048576).toFixed(2) + "MB";
					} else {
						that.fileSizeString = (sizeCache / 1073741824).toFixed(2) + "GB";
					}
				});
				// #endif
			},
			// 清除缓存
			clern() {
				let that = this
				// #ifdef APP-PLUS
				uni.showModal({
					title: '清除缓存',
					content: '您确定要清除缓存吗？',
					success: function(res) {
						if (res.confirm) {
							console.log('用户点击确定');
							that.clearCache()
						} else if (res.cancel) {
							console.log('用户点击取消');
						}
					}
				});
				// #endif
			},
			// 清理缓存
			clearCache() {
				let that = this;
				uni.showLoading({
					mask: true,
					title: "清除中..."
				})
				// #ifdef APP-PLUS
				let os = plus.os.name;
				if (os == 'Android') {
					let main = plus.android.runtimeMainActivity();
					let sdRoot = main.getCacheDir();
					let files = plus.android.invoke(sdRoot, "listFiles");
					let len = files.length;
					for (let i = 0; i < len; i++) {
						let filePath = '' + files[i]; // 没有找到合适的方法获取路径，这样写可以转成文件路径  
						plus.io.resolveLocalFileSystemURL(filePath, function(entry) {
							if (entry.isDirectory) {
								entry.removeRecursively(function(entry) { //递归删除其下的所有文件及子目录  
									uni.hideLoading();
									uni.showToast({
										title: '缓存清理完成',
										duration: 2000
									});
									that.formatSize(); // 重新计算缓存
								}, function(e) {
									console.log(e.message)
								});
							} else {
								entry.remove();
							}
						}, function(e) {
							console.log('文件路径读取失败')
						});
					}
				} else { // ios  
					plus.cache.clear(function() {
						uni.showToast({
							title: '缓存清理完成',
							duration: 2000
						});
						that.formatSize();
					});
				}
				// #endif
			}
		}
	}
</script>
```
