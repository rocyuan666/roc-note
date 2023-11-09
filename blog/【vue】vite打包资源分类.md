# 参考文档

配置rollup output选项，官方文档参考：  
[构建选项 | Vite 官方中文文档 (vitejs.dev)](https://cn.vitejs.dev/config/build-options.html#build-rollupoptions)  
[Configuration Options | Rollup (rollupjs.org)](https://rollupjs.org/configuration-options/#output-chunkfilenames)  
[Configuration Options | Rollup (rollupjs.org)](https://rollupjs.org/configuration-options/#output-entryfilenames)  
[Configuration Options | Rollup (rollupjs.org)](https://rollupjs.org/configuration-options/#output-assetfilenames)  

# 配置

```javascript
build: {
  rollupOptions: {
    output: {
		chunkFileNames: 'static/js/[name]-[hash].js',
		entryFileNames: 'static/js/[name]-[hash].js',
		assetFileNames: 'static/[ext]/[name]-[hash].[ext]'
    }
  }
},
```
