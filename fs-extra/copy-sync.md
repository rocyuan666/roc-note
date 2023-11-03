# copySync(src, dest[, options])

复制文件或目录。目录可以包含内容。

- `src` `<String>` 注意，如果src是一个目录，它将复制该目录中的所有内容，而不是整个目录本身。
- `dest` `<String>` 注意，如果src是文件，则dest不能是目录
- `options` `<Object>` 
   - `overwrite` `<boolean>`: 覆盖现有文件或目录，默认值为true。请注意，如果将此设置为false并且目标存在，则复制操作将自动失败。使用errorOnExist选项更改此行为。
   - `errorOnExist` `<boolean>`: 当overwrite为false并且目标存在时，抛出错误。默认值为false。
   - `dereference` `<boolean>`: 取消引用符号链接，默认值为false。
   - `preserveTimestamps` `<boolean>`: 如果为true，将设置对原始源文件的最后修改和访问时间。如果为false，则时间戳行为取决于操作系统。默认值为false。
   - `filter` `<Function>`: 用于过滤复制的文件/目录的函数。返回true复制项目，返回false忽略项目。

## Example:

```javascript
const fs = require('fs-extra')

// 复制文件
fs.copySync('/tmp/myfile', '/tmp/mynewfile')

// 复制目录，即使它有子目录或文件
fs.copySync('/tmp/mydir', '/tmp/mynewdir')
```

**Using filter function**

```javascript
const fs = require('fs-extra')

const filterFunc = (src, dest) => {
  // 你的逻辑在这里
  // 如果返回true，将复制它
}

fs.copySync('/tmp/mydir', '/tmp/mynewdir', { filter: filterFunc })
```
