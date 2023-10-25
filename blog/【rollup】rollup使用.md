项目中使用的开源插件需要进行二次开发，插件源码生产环境使用rollup打包构建，学习了下rollup，记录下。
# 安装rollup
```javascript
npm install -D rollup
```
# rollup打包
package.json配置脚本
```json
"scripts": {
  "build:lib": "rollup -c rollup.config.js"
},
```
# 配置文件
项目根目创建`rollup.config.js`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663726712351-37329b4b-2ad5-495e-aa12-01f5e91ce064.png#averageHue=%239eb37b&clientId=uec735bcd-f458-4&errorMessage=unknown%20error&from=paste&height=597&id=uc489d8d8&originHeight=597&originWidth=913&originalType=binary&ratio=1&rotation=0&showTitle=false&size=71611&status=error&style=none&taskId=u889d3422-aed0-4e3b-81d6-078f768a255&title=&width=913)
# 配置项
## 常用配置
详细配置参考官网
中文站：[https://www.rollupjs.com/guide/big-list-of-options](https://www.rollupjs.com/guide/big-list-of-options)
英文官网：[https://rollupjs.org/guide/en/#big-list-of-options](https://rollupjs.org/guide/en/#big-list-of-options)
### input
入口文件
```javascript
{
  input: "./lib/index.js",
}
```
### output
出口文件，当需要打多个js包时（xxx.js 与 xxx.min.js）传数组
#### file
要写入的文件
#### dir
放置所有生成的块的目录。如果生成多个块，则需要此选项。否则，可以使用`file`选项。
#### format
支持六种输出格式：amd / cjs /es / iife / umd / system(不常用，但官网有)
#### name
当`format`为`iife`和`umd`时必须提供，将作为全局变量挂在window(浏览器环境)下：window[name值]=...
#### entryFileNames
打包资源名格式配置，默认[name].js，一共三种格式 format / hash:长度 / name
#### banner
打包到块中的字符串，常用与顶部文档注释
```javascript
const { terser } = require("rollup-plugin-terser");

{
  output: [
    {
      dir: 'dist',
      name: "Roc",
      entryFileNames: 'roc.min.js',
      format: "umd",
      banner: "/** 文档注释... */",
      plugins: [
        terser()
      ], // 给这个出口文件 单独配置插件
    }
    // ...
  ]
}
```
### external
告诉rollup不要将 某些库(下列示例：jquery) 打包，而作为外部依赖。
```javascript
{
  external: ["jquery"]
}
```
### globals
告诉 `rollup` `jquery` 是外部依赖，并且 `jquery` 模块的 ID 为全局变量 `$`
```javascript
{
  "jquery": "$"
}
```
### plugins
rollup插件配置，比如引入压缩代码插件
```javascript
const { terser } = require("rollup-plugin-terser");

{
  plugins: [
    terser()
  ]
}
```
`plugins`配置，需要熟悉很多rollup插件的用途及配置。
# rollup插件
记录使用到的插件，官方github或npm仓库链接地址中有详细配置说明。
## @rollup/plugin-buble
[https://github.com/rollup/plugins/tree/master/packages/buble/#readme](https://github.com/rollup/plugins/tree/master/packages/buble/#readme)
使用Buble编译器转换ES6+代码的插件。
## @rollup/plugin-commonjs
[https://github.com/rollup/plugins/tree/master/packages/commonjs/#readme](https://github.com/rollup/plugins/tree/master/packages/commonjs/#readme)
用于将CommonJS模块转换为ES6
## **@rollup/plugin-terser**
[https://github.com/rollup/plugins/tree/master/packages/terser#readme](https://github.com/rollup/plugins/tree/master/packages/terser#readme)
Rollup插件，用于生成精简的js包（min.js）
## rollup-plugin-javascript-obfuscator
[https://www.npmjs.com/package/rollup-plugin-javascript-obfuscator](https://www.npmjs.com/package/rollup-plugin-javascript-obfuscator)
js代码混淆处理插件
## @rollup/plugin-babel
[https://github.com/rollup/plugins/tree/master/packages/babel#readme](https://github.com/rollup/plugins/tree/master/packages/babel#readme)
用于Rollup和Babel之间的无缝集成。
## @rollup/plugin-node-resolve
[https://github.com/rollup/plugins/tree/master/packages/node-resolve/#readme](https://github.com/rollup/plugins/tree/master/packages/node-resolve/#readme)
在node_modules中查找并捆绑第三方依赖项（使用后会将使用到的第三方依赖打包进来，不需要打包进来配合选项“external”使用）
## @rollup/plugin-replace
[https://github.com/rollup/plugins/tree/master/packages/replace#readme](https://github.com/rollup/plugins/tree/master/packages/replace#readme)
打包时替换文件中的字符串
## rollup-plugin-node-externals
[https://github.com/Septh/rollup-plugin-node-externals#readme](https://github.com/Septh/rollup-plugin-node-externals#readme)
在汇总配置中自动将NodeJS内置模块和npm依赖项声明为“external（外部）”
## rollup-plugin-postcss
[https://github.com/egoist/rollup-plugin-postcss#readme](https://github.com/egoist/rollup-plugin-postcss#readme)
Rollup和PostCSS之间的无缝集成。
## rollup-plugin-visualizer
[https://github.com/btd/rollup-plugin-visualizer](https://github.com/btd/rollup-plugin-visualizer)
可视化并分析Rollup打包，以查看哪些模块正在占用空间。
## rollup-plugin-vue
[https://www.npmjs.com/package/rollup-plugin-vue](https://www.npmjs.com/package/rollup-plugin-vue)
vue SFC（.vue文件）处理
## vue-template-compiler
[https://www.npmjs.com/package/vue-template-compiler](https://www.npmjs.com/package/vue-template-compiler)
Vue 2.0模板编译器
## @rollup/plugin-typescript
[https://www.npmjs.com/package/@rollup/plugin-typescript](https://www.npmjs.com/package/@rollup/plugin-typescript)
Rollup插件用于Rollup和Typescript之间的无缝集成。（依赖 tslib 模块 `npm install -D tslib`）
# 参考
## react-redux官方rollup配置
react-redux库rollup配置文件：
[https://github.com/reduxjs/react-redux/blob/master/rollup.config.js](https://github.com/reduxjs/react-redux/blob/master/rollup.config.js)
```javascript
import nodeResolve from '@rollup/plugin-node-resolve'
import babel from '@rollup/plugin-babel'
import replace from '@rollup/plugin-replace'
import commonjs from '@rollup/plugin-commonjs'
import { terser } from 'rollup-plugin-terser'
import pkg from './package.json'

const env = process.env.NODE_ENV

const extensions = ['.js', '.ts', '.tsx', '.json']

const config = {
  input: 'src/index.ts',
  external: Object.keys(pkg.peerDependencies || {}).concat('react-dom'),
  output: {
    format: 'umd',
    name: 'ReactRedux',
    globals: {
      react: 'React',
      redux: 'Redux',
      'react-dom': 'ReactDOM',
    },
  },
  plugins: [
    nodeResolve({
      extensions,
    }),
    babel({
      include: 'src/**/*',
      exclude: '**/node_modules/**',
      babelHelpers: 'runtime',
      extensions,
    }),
    replace({
      'process.env.NODE_ENV': JSON.stringify(env),
      preventAssignment: true,
    }),
    commonjs(),
  ],
}

if (env === 'production') {
  config.plugins.push(
    terser({
      compress: {
        pure_getters: true,
        unsafe: true,
        unsafe_comps: true,
        warnings: false,
      },
    })
  )
}

export default config
```
