执行nrm报错 internal/validators.js:124 throw new ERR_INVALID_ARG_TYPE(name, ‘string’, value);
```javascript
C:\Users\Administrator>nrm ls
internal/validators.js:124
    throw new ERR_INVALID_ARG_TYPE(name, 'string', value);
    ^
[TypeError [ERR_INVALID_ARG_TYPE]: The "path" argument must be of type string. Received undefined
  at validateString (internal/validators.js:124:11)
  at Object.join (path.js:375:7)
  at Object.<anonymous> (D:\nodejs\node_global\node_modules\nrm\cli.js:17:20)
  at Module._compile (internal/modules/cjs/loader.js:1063:30)
  at Object.Module._extensions..js (internal/modules/cjs/loader.js:1092:10)
  at Module.load (internal/modules/cjs/loader.js:928:32)
  at Function.Module._load (internal/modules/cjs/loader.js:769:14)
  at Function.executeUserEntryPoint [as runMain] (internal/modules/run_main.js:72:12)
  at internal/main/run_main_module.js:17:47
] {
  code: 'ERR_INVALID_ARG_TYPE'
}
```
找到安装nrm的文件夹，一般在（AppData为隐藏文件夹）：
```javascript
C:\Users\Administrator\AppData\Roaming\npm\node_modules\nrm
```
找到cli.js17行，改成：
```javascript
//const NRMRC = path.join(process.env.HOME, '.nrmrc'); (删除)
const NRMRC = path.join(process.env[(process.platform == 'win32') ? 'USERPROFILE' : 'HOME'], '.nrmrc');
```
