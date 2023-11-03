# outputJsonSync(file, object[, options])

与writeJsonSync几乎相同，只是如果目录不存在，则会创建它。

**Alias:** `outputJSONSync()`

- `file` `<String>`
- `object` `<Object>`
- `options` `<Object>` 
   - `spaces` `<Number> | <String>` 要缩进的空格数；或用于缩进的字符串（即传递“\t”用于制表符缩进）。有关更多信息，请[参阅文档](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify#The_space_argument)。
   - `EOL` `<String>` 设置EOL字符。默认值为\n。
   - `replacer` [JSON replacer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify#The_replacer_parameter)
   - 也接受 `[fs.writeFileSync()](https://nodejs.org/api/fs.html#fs_fs_writefilesync_file_data_options)`[ options](https://nodejs.org/api/fs.html#fs_fs_writefilesync_file_data_options)

## Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/this/path/does/not/exist/file.json'
fs.outputJsonSync(file, {name: 'JP'})

const data = fs.readJsonSync(file)
console.log(data.name) // => JP
```
