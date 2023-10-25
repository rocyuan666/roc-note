> 作者：yuxiaoliang
链接：https://juejin.cn/post/7099041402771734559
来源：稀土掘金

npm是前端开发人员广泛使用的包管理工具，项目中通过package.json来管理项目中所依赖的npm包的配置。package.json就是一个json文件，除了能够描述项目的包依赖外，允许我们使用“语义化版本规则”指明你项目依赖包的版本，让你的构建更好地与其他开发者分享，便于重复使用。     本文主要从最近的实践出发，结合最新的npm和node的版本，介绍一下package.json中一些常见的配置以及如何写一个规范的package.json
> - package.json
> - package.json常用属性
> - package.json环境相关属性
> - package.json依赖相关属性
> - package.json三方属性

## 一、package.json
### 1. package.json简介
在nodejs项目中，package.json是管理其依赖的配置文件，通常我们在初始化一个nodejs项目的时候会通过：
```bash
npm init
```
然后在你的目录下会生成3个目录/文件， node_modules, package.json和 package.lock.json。其中package.json的内容为：
```javascript
{
    "name": "Your project name",
    "version": "1.0.0",
    "description": "Your project description",
    "main": "app.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
    },
    "author": "Author name",
    "license": "ISC",
    "dependencies": {
        "dependency1": "^1.4.0",
        "dependency2": "^1.5.2"
    }
}
```
上述可以看出，package.json中包含了项目本身的元数据,以及项目的子依赖信息(比如dependicies等)。
### 2. package-lock.json
我们发现在npm init的时候，不仅生成了package.json文件，还生成了package-lock.json文件。那么为什么存在package.json的清空下，还需要生成package-lock.json文件呢。本质上package-lock.json文件是为了锁版本，在package.json中指定的子npm包比如：react: "^16.0.0"，在实际安装中，只要高于react的版本都满足package.json的要求。这样就使得根据同一个package.json文件，两次安装的子依赖版本不能保证一致。
而package-lock文件如下所示，子依赖dependency1就详细的指定了其版本。起到lock版本的作用。
```javascript
{
    "name": "Your project name",
    "version": "1.0.0",
    "lockfileVersion": 1,
    "requires": true,
    "dependencies": {
        "dependency1": {
            "version": "1.4.0",
            "resolved": 
"https://registry.npmjs.org/dependency1/-/dependency1-1.4.0.tgz",
            "integrity": 
"sha512-a+UqTh4kgZg/SlGvfbzDHpgRu7AAQOmmqRHJnxhRZICKFUT91brVhNNt58CMWU9PsBbv3PDCZUHbVxuDiH2mtA=="
        },
        "dependency2": {
            "version": "1.5.2",
            "resolved": 
"https://registry.npmjs.org/dependency2/-/dependency2-1.5.2.tgz",
            "integrity": 
"sha512-WOn21V8AhyE1QqVfPIVxe3tupJacq1xGkPTB4iagT6o+P2cAgEOOwIxMftr4+ZCTI6d551ij9j61DFr0nsP2uQ=="
        }
    }
}
```
## 二、package.json常用属性
本章来聊聊package.json中常用的配置属性，形如name，version等属性太过简单，不一一介绍。本章主要介绍一下script、bin和workspaces属性。
### 2.1 script
在npm中使用script标签来定义脚本，每当制定npm run的时候，就会自动创建一个shell脚本，这里需要注意的是，npm run新建的这个 Shell，会将本地目录的node_modules/.bin子目录加入PATH变量。
这意味着，当前目录的node_modules/.bin子目录里面的所有脚本，都可以直接用脚本名调用，而不必加上路径。比如，当前项目的依赖里面有 esbuild，只要直接写esbuild xxx 就可以了。
```javascript
{
  // ...
  "scripts": {
    "build": "esbuild index.js",
  }
}
```
```javascript
{
  // ...
  "scripts": {
    "build": "./node_modules/.bin/esbuild index.js" 
  }
}
```
上面两种写法是等价的。
### 2.2 bin
bin属性用来将可执行文件加载到全局环境中，指定了bin字段的npm包，一旦在全局安装，就会被加载到全局环境中，可以通过别名来执行该文件。
比如@bytepack/cli的npm包：
```javascript
"bin": {
    "bytepack": "./bin/index.js"
 },
```
一旦在全局安装了@bytepack/cli，就可以直接通过bytepack来执行相应的命令，比如
```bash
bytepack -v
//显示1.11.0
```
如果非全局安装，那么会自动连接到项目的node_module/.bin目录中。与前面介绍的script标签中所说的一致，可以直接用别名来使用。
### 2.3 workspaces
在项目过大的时候，最近越来越流行monorepo。提到monorepo就绕不看workspaces，早期我们会用yarn workspaces，现在npm官方也支持了workspaces.     workspaces解决了本地文件系统中如何在一个顶层root package下管理多个子packages的问题，在workspaces声明目录下的package会软链到最上层root package的node_modules中。
直接以官网的例子来说明：
```javascript
{
  "name": "my-project",
    "workspaces": [
    "packages/a"
  ]
}
```
在一个npm包名为my-project的npm包中，存在workspaces配置的目录。
```javascript
.
+-- package.json
+-- index.js
`-- packages
   +-- a
   |  `-- package.json

```
并且该最上层的名为my-project的root包，有packages/a子包。此时，我们如果npm install,那么在root package中node_modules中安装的npm包a，指向的是本地的package/a.
```javascript
.
+-- node_modules
|  `-- packages/a -> ../packages/a
+-- package-lock.json
+-- package.json
`-- packages
   +-- a
   |   `-- package.json
```
上述的
```javascript
-- packages/a -> ../packages/a
```
指的就是从node_modules中a链接到本地npm包的软链
## 三、package.json环境相关属性
常见的环境，基本上分为浏览器browser和node环境两大类，接下来我们来看看package.json中，跟环境相关的配置属性。环境的定义可以简单理解如下：

- browser环境：比如存在一些只有在浏览器中才会存在的全局变量等，比如window，Document等
- node环境: npm包的源文件中存在只有在node环境中才会有的一些变量和内置包，内置函数等。
### 3.1 type
js的模块化规范包含了commonjs、CMD、UMD、AMD和ES module等，最早先在node中支持的仅仅是commonjs字段，但是从node13.2.0开始后，node正式支持了ES module规范，在package.json中可以通过type字段来声明npm包遵循的模块化规范。
```javascript
//package.json
{
   name: "some package",
   type: "module"||"commonjs" 
}

```
需要注意的是：

- 不指定type的时候，type的默认值是commonjs，不过建议npm包都指定一下type
- 当type字段指定值为module则采用ESModule规范
- 当type字段指定时，目录下的所有.js后缀结尾的文件，都遵循type所指定的模块化规范
- 除了type可以指定模块化规范外，通过文件的后缀来指定文件所遵循的模块化规范，以.mjs结尾的文件就是使用的ESModule规范，以.cjs结尾的遵循的是commonjs规范
### 3.2 main & module & browser
除了type外，package.json中还有main,module和browser 3个字段来定义npm包的入口文件。

- main : 定义了 npm 包的入口文件，browser 环境和 node 环境均可使用
- module : 定义 npm 包的 ESM 规范的入口文件，browser 环境和 node - 环境均可使用
- browser : 定义 npm 包在 browser 环境下的入口文件

我们来看一下这3个字段的使用场景，以及同时存在这3个字段时的优先级。我们假设有一个npm包为demo1,
```javascript
----- dist
   |-- index.browser.js
   |-- index.browser.mjs
   |-- index.js
   |-- index.mjs
```
其package.json中同时指定了main,module和browser这3个字段，
```javascript
  "main": "dist/index.js",  // main 
  "module": "dist/index.mjs", // module

  // browser 可定义成和 main/module 字段一一对应的映射对象，也可以直接定义为字符串
  "browser": {
    "./dist/index.js": "./dist/index.browser.js", // browser+cjs
    "./dist/index.mjs": "./dist/index.browser.mjs"  // browser+mjs
  },

  // "browser": "./dist/index.browser.js" // browser
```
默认构建和使用，比如我们在项目中引用这个npm包：
```javascript
import demo from 'demo'
```
通过构建工具构建上述代码后，模块的加载循序为：
_**browser+mjs > module > browser+cjs > main**_
这个加载顺序是大部分构建工具默认的加载顺序，比如webapck、esbuild等等。可以通过相应的配置修改这个加载顺序，不过大部分场景，我们还是会遵循默认的加载顺序。
### 3.3 exports
如果在package.json中定义了exports字段，那么这个字段所定义的内容就是该npm包的真实和全部的导出，优先级会高于main和file等字段。
举例来说：
```javascript
{
  "name": "pkg",
  "exports": {
    ".": "./main.mjs",
    "./foo": "./foo.js"
  }
}
```
```javascript
import { something } from "pkg"; // from "pkg/main.mjs"
```
```javascript
const { something } = require("pkg/foo"); // require("pkg/foo.js")
```
从上述的例子来看，exports可以定义不同path的导出。如果存在exports后，以前正常生效的file目录到处会失效，比如require('pkg/package.json')，因为在exports中没有指定，就会报错。
exports还有一个最大的特点，就是条件引用，比如我们可以根据不同的引用方式或者模块化类型，来指定npm包引用不同的入口文件。
```javascript
// package.json
{ 
  "name":"pkg",
  "main": "./main-require.cjs",
  "exports": {
    "import": "./main-module.js",
    "require": "./main-require.cjs"
  },
  "type": "module"
}
```
上述的例子中，如果我们通过
```javascript
const p = require('pkg')
```
引用的就是"./main-require.cjs"。
如果通过：
```javascript
import p from 'pkg'
```
引用的就是"./main-module.js"
最后需要注意的是 ： _**如果存在exports属性，exports属性不仅优先级高于main，同时也高于module和browser字段。**_
## 四、package.json依赖相关属性
package.json中跟依赖相关的配置属性包含了dependencies、devDependencies、peerDependencies和peerDependenciesMeta等。
dependencies是项目的依赖，而devDependencies是开发所需要的模块，所以我们可以在开发过程中需要的安装上去，来提高我们的开发效率。这里需要注意的时，在自己的项目中尽量的规范使用，形如webpack、babel等是开发依赖，而不是项目本身的依赖，不要放在dependencies中。
dependencies除了dependencies和devDependencies，本文重点介绍的是peerDependencies和peerDependenciesMeta。
### 4.1 peerDependencies
peerDependencies是package.json中的依赖项,可以解决核心库被下载多次，以及统一核心库版本的问题。
```javascript
//package/pkg
----- node_modules
   |-- npm-a -> 依赖了react,react-dom
   |-- npm-b -> 依赖了react,react-dom
   |-- index.js
```
比如上述的例子中如果子npm包a,b都以来了react和react-dom,此时如果我们在子npm包a,b的package.json中声明了PeerDependicies后，相应的依赖就不会重新安装。
需要注意的有两点：

- 对于子npm包a,在npm7中，如果单独安装子npm a,其peerDependicies中的包，会被安装下来。但是npm7之前是不会的。
- 请规范和详细的指定PeerDependicies的配置，笔者在看到有些react组件库，不在PeerDependicies中指定react和react-dom，或者将react和react-dom放到了dependicies中，这两种不规范的指定都会存在一些问题。
- 其二，正确的指定PeerDependicies中npm包的版本，[react-focus-lock@2.8.1](https://link.juejin.cn?target=mailto%3Areact-focus-lock%402.8.1),peerDependicies指定的是："react": "^16.8.0 || ^17.0.0 || ^18.0.0"，但实际上，这个react-focus-lock并不支持18.x的react
### 4.2 peerDependenciesMeta
看到“Meta”就有元数据的意思，这里的peerDependenciesMeta就是详细修饰了peerDependicies，比如在react-redux这个npm包中的package.json中有这么一段：
```javascript
 "peerDependencies": {
    "react": "^16.8.3 || ^17 || ^18"
  },
 "peerDependenciesMeta": {
    "react-dom": {
      "optional": true
    },
    "react-native": {
      "optional": true
    }
  }
```
这里指定了"react-dom","react-native"在peerDependenciesMeta中，且为可选项，因此如果项目中检测没有安装"react-dom"和"react-native"都不会报错。
值得注意的是，通过peerDependenciesMeta我们确实是取消了限制，但是这里经常存在非A即B的场景，比如上述例子中，我们需要的是“react-dom”和"react-native"需要安装一个，但是实际上通过上述的声明，我们实现不了这种提示。
## 五、package.json三方属性
package.json中也存在很多三方属性，比如tsc中使用的types、构建工具中使用的sideEffects,git中使用的husky，eslint使用的eslintIgnore，这些扩展的配置，针对特定的开发工具是有意义的这里不一一举例。

