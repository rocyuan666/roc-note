# outputFileSync(file, data[, options])

几乎与writeFileSync相同（即重写），只是如果父目录不存在，则会创建它。文件必须是文件路径（不允许使用缓冲区或文件描述符）。

- `file` `<String>`
- `data` `<String> | <Buffer> | <Uint8Array>`
- `options` `<Object> | <String>` (与 `[fs.writeFileSync()](https://nodejs.org/api/fs.html#fs_fs_writefilesync_file_data_options)`[ options](https://nodejs.org/api/fs.html#fs_fs_writefilesync_file_data_options) 一样 )

## Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/this/path/does/not/exist/file.txt'
fs.outputFileSync(file, 'hello!')

const data = fs.readFileSync(file, 'utf8')
console.log(data) // => hello!
```
