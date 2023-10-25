# 前言
文章中的演示上传的并非npm官网仓库，只是npm源不同而已。
# 准备ui库项目
## 创建项目
使用vue-cli准备一个vue项目进行改造，创建项目过程不在演示 vue create xxx
## 修改依赖
创建完成后，我们将`package.json`生产时依赖改到开发时依赖（因为我们是开发库文件，不应该将vue等打包到库项目中），然后重新安装依赖，重新安装依赖前，个人删除了`node_modules文件夹`与npm锁定文件`package.lock.json`。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663293831955-9c9b39ab-ed7b-4746-a8c7-f8c991eedfb7.png#clientId=u559430fa-f46f-4&errorMessage=unknown%20error&from=paste&height=645&id=u331e61b9&originHeight=645&originWidth=882&originalType=binary&ratio=1&rotation=0&showTitle=false&size=126844&status=error&style=none&taskId=uf6c7c5aa-1da7-4c80-9aea-5c3906cf361&title=&width=882)
## 目录修改与vue脚手架配置
默认情况下vue-cli创建项目入口目录是`src`，我们参考`element-ui`目录结构，将`src`更改为`examples`作为项目演示目录。再新建目录`packages`作为库文件组件存放目录。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663295117616-289ca2ef-e5ac-4202-9bda-c5ccbadf840c.png#clientId=u559430fa-f46f-4&errorMessage=unknown%20error&from=paste&height=601&id=u0d6e31d0&originHeight=601&originWidth=1020&originalType=binary&ratio=1&rotation=0&showTitle=false&size=149301&status=error&style=none&taskId=u3be5f09b-271a-4413-a833-fc8f2d1a9c9&title=&width=1020)
```javascript
module.exports = defineConfig({
  transpileDependencies: true,
  productionSourceMap: false,
  // 配置参考：https://cli.vuejs.org/zh/config/#pages
  pages: {
    index: {
      // 入口
      entry: "examples/main.js",
      // 模板
      template: "public/index.html",
      // 打包输出的html
      filename: "index.html",
    },
  },
  // 配置参考：https://cli.vuejs.org/zh/config/#chainwebpack
  chainWebpack: (config) => {
    config.module
      .rule("js")
      .include.add("/packages")
      .end()
      .use("babel")
      .loader("babel-loader");
  },
});

```
## 配置脚本构建目标
参考：[https://cli.vuejs.org/zh/guide/build-targets.html](https://cli.vuejs.org/zh/guide/build-targets.html)
vue-cli默认构建目标是应用，需要修改为库，`--target lib`指定为构建为库，`--name rocyuan-ui`指定名字，`--dest lib`指定构建完的目录，`packages/index.js`指定构建入口，稍后开发完组件运行这个脚本
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663295749107-f29e6da9-ef64-4884-bb83-ac56f07599b4.png#clientId=u559430fa-f46f-4&errorMessage=unknown%20error&from=paste&height=521&id=u923171b4&originHeight=521&originWidth=1032&originalType=binary&ratio=1&rotation=0&showTitle=false&size=83594&status=error&style=none&taskId=u00d6d870-afd3-4a16-86a5-7d606dc3c9c&title=&width=1032)
```java
"lib": "vue-cli-service build --target lib --name rocyuan-ui --dest lib packages/index.js"
```
# 开始写组件
## 组件目录划分
例如写一个input组件，目录结构及写法借鉴element-ui
在`packages`目录创建`index.js`入口，创建`input`目录，其他组件则创建其他组件的目录，组件目录分`index.js`入口文件与`src`目录组件封装源文件目录
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663298612275-f25a1d74-8dd6-487c-907a-274cd5d0128d.png#clientId=u559430fa-f46f-4&errorMessage=unknown%20error&from=paste&height=786&id=ufd288d6a&originHeight=786&originWidth=1050&originalType=binary&ratio=1&rotation=0&showTitle=false&size=143202&status=error&style=none&taskId=u32df2d9b-51a5-442b-9ef7-a993d8abbbf&title=&width=1050)
## 组件代码
packages/index.js
```javascript
import RocInput from "./input";

const components = [RocInput];
// 定义 install 方法，使用use方法注册需要暴露 install 方法（参考vue官网 use方法）
const install = (Vue) => {
  if (install.installed) return;
  install.installed = true
  components.map((component) => Vue.component(component.name, component));
};
// 判断是否是直接引入文件
if (typeof window !== "undefined" && window.Vue) {
  install(window.Vue);
}
export default {
  install,
  ...components,
};


```
packages/input/index.js
```javascript
import Button from "./src/main";

Button.install = (Vue) => {
  Vue.component(Button.name, Button);
};

export default Button;
```
packages/input/src/main.vue
```javascript
<template>
  <div class="roc-input">
    <input type="text"
      :maxlength="maxlength"
      :value="value"
      @input="handleInput"
      :style="{
        borderColor: borderColor,
        borderRadius: borderRadius
      }"
    >
  </div>
</template>

<script>
export default {
  name: "RocInput",
  props: {
    value: {
      type: String
    },
    maxlength: {
      type: Number,
    },
    borderColor: {
      type: String,
      default: '#ddd'
    },
    borderRadius: {
      type: String,
      default: '20px'
    }
  },
  methods: {
    handleInput(e) {
      this.$emit("input", e.target.value)
    }
  }
}
</script>

<style lang="scss" scoped>
.roc-input {
  input {
    outline: none;
    padding: 5px 10px;
    margin: 4px 0;
  }
}
</style>

```
## 库项目中调试效果
引入packages/index.js，在examples/main.js中引入并注册，然后使用（与平时在项目中使用一致），启动项目后查看效果（必须修改上面提到的脚手架配置）`npm run serve`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663299173410-2810b37a-043c-48fa-a90f-20062e160875.png#clientId=u5da898ef-51eb-4&errorMessage=unknown%20error&from=paste&height=641&id=ua44fdadf&originHeight=641&originWidth=959&originalType=binary&ratio=1&rotation=0&showTitle=false&size=108478&status=error&style=none&taskId=u547107b3-b26a-4623-ae8b-81bb413bfb3&title=&width=959)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663299249893-a4a0ded1-9364-4361-9de8-e33306eab9dc.png#clientId=u5da898ef-51eb-4&errorMessage=unknown%20error&from=paste&height=629&id=u14e0cf3d&originHeight=629&originWidth=1192&originalType=binary&ratio=1&rotation=0&showTitle=false&size=119320&status=error&style=none&taskId=ua6888818-78e6-4c80-9b68-5ba39084dbe&title=&width=1192)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663299517818-7cbcffa9-8559-4f78-a4e7-dc6d816c0e68.png#clientId=u5da898ef-51eb-4&errorMessage=unknown%20error&from=paste&height=188&id=u16e3ec41&originHeight=188&originWidth=552&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13035&status=error&style=none&taskId=u385269e4-4fab-4e5c-881e-2f044dd5915&title=&width=552)
# 上传npm
## 上传前配置
### 设置package.json
运行`npm run lib`后 会收件生成ui库，在lib目录，设置`package.json`中设置描述、关键字、及入口文件：
```javascript
"description": "roc-ui",
"main": "lib/rocyuan-ui.umd.min.js",
"keyword": "rocyuan roc-ui vue",
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663299959090-834513c2-480a-4465-a9b9-441eb70cdbea.png#clientId=u5da898ef-51eb-4&errorMessage=unknown%20error&from=paste&height=721&id=PwwKd&originHeight=721&originWidth=1505&originalType=binary&ratio=1&rotation=0&showTitle=false&size=180463&status=error&style=none&taskId=u55fce3fe-7ab1-461c-85c2-d3433db0469&title=&width=1505)
### 设置上传npm忽略的文件
项目根目录下创建`.npmignore`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663300442490-b6cc6b58-2277-415d-a480-53029e18f661.png#clientId=u5da898ef-51eb-4&errorMessage=unknown%20error&from=paste&height=597&id=u45092e58&originHeight=597&originWidth=712&originalType=binary&ratio=1&rotation=0&showTitle=false&size=87922&status=error&style=none&taskId=u0a29aaf4-75e3-4b97-a247-b9fdad9b8fd&title=&width=712)
```javascript

# 忽略目录
examples/
packages/
public/
node_modules/
 
# 忽略指定文件
vue.config.js
babel.config.js
*.map

```
## npm设置
上传前需要在命令行登陆npm（注意确保你的npm当前源是你想上传的源）查看当前源：`npm get registry`
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663300694528-19b0ae08-684a-4ca2-a8ac-77a78c67ee24.png#clientId=u5da898ef-51eb-4&errorMessage=unknown%20error&from=paste&height=103&id=u786b368b&originHeight=103&originWidth=535&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13453&status=error&style=none&taskId=u5e3e72b4-39ac-4b50-a1e6-ea16443bf2d&title=&width=535)
我是要上传私有仓库，官方仓库源应该为：https://registry.npmjs.org/，如何切换源，登陆，查看登陆，发布等更多的命令详情参考[【npm】从入门到私服搭建](https://www.yuque.com/rocyuan/blog/sw8efu)
注意：如果需要登陆、提交的源本身就是当前npm设置的源，不需要指定源 --registry http://xxxxxxxxxx
确定源后使用`npm login`登陆登陆成功后，可使用`npm whoami`查看当前登陆的账号
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663308565404-1c90f244-d998-4152-9918-a9b4cf598292.png#clientId=u9f2a6de2-966b-4&from=paste&height=93&id=u905a85ae&originHeight=93&originWidth=593&originalType=binary&ratio=1&rotation=0&showTitle=false&size=15205&status=done&style=none&taskId=u2580cc47-68ae-4a75-8ae6-f5635f9cdd3&title=&width=593)
登陆成功后使用`npm publish`发布到npm，发布完成后如下：
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663308637028-aa2e1a78-dcac-47fd-9392-721f5b1570c5.png#clientId=u9f2a6de2-966b-4&from=paste&height=438&id=ub79d6f62&originHeight=438&originWidth=578&originalType=binary&ratio=1&rotation=0&showTitle=false&size=88406&status=done&style=none&taskId=u45e9f1e0-6485-41ae-b864-ddbcbb9721c&title=&width=578)
# 使用我们上传的ui库
创建vue项目不做演示，已创建好
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663313954620-72129eec-ed2d-4163-b90f-c479db34eded.png#clientId=u9f2a6de2-966b-4&from=paste&height=700&id=u3e56d1b4&originHeight=700&originWidth=820&originalType=binary&ratio=1&rotation=0&showTitle=false&size=64535&status=done&style=none&taskId=u934576da-e298-4276-ae35-76abcb4c6cb&title=&width=820)
安装使用
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663314244376-cd349251-fd9b-4c19-9a30-c3d8e285b74b.png#clientId=u9f2a6de2-966b-4&from=paste&height=734&id=u50d7342c&originHeight=734&originWidth=1610&originalType=binary&ratio=1&rotation=0&showTitle=false&size=250532&status=done&style=none&taskId=u0a16e557-f0b6-4629-a218-beb76b208f3&title=&width=1610)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/2779910/1663314285147-0bf428a3-b2c7-4d6b-8eb0-e8e3f5a8e818.png#clientId=u9f2a6de2-966b-4&from=paste&height=858&id=ud68e186e&originHeight=858&originWidth=1518&originalType=binary&ratio=1&rotation=0&showTitle=false&size=80337&status=done&style=none&taskId=ua867c67e-4a54-47ee-b94d-aede8d7bebd&title=&width=1518)

