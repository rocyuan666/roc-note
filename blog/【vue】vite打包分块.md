# 参考文档

配置rollup output选项，官方文档参考：  
[vite chunk 大小警告配置](https://cn.vitejs.dev/config/build-options.html#build-chunksizewarninglimit)  
[vite rollup 打包配置](https://cn.vitejs.dev/config/build-options.html#build-rollupoptions)  
[rollup 输出chunk配置](https://rollupjs.org/configuration-options/#output-manualchunks)  

# 配置

```javascript
build: {
  chunkSizeWarningLimit: 1024,
  rollupOptions: {
	output: {
	  manualChunks: {
		monacoeditor: ["monaco-editor"],
		quill: ["quill"],
		lodash: ["lodash"],
		lib: ["sortablejs", "vxe-table", "xe-utils"],
		vlib: ["vue", "vue-router", "vue-i18n", "element-plus"]
	  }
	}
  }
}
```