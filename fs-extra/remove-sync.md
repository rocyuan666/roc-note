# removeSync(path)

删除文件或目录。目录可以包含内容。如果路径不存在，则不执行任何操作。

- `path` `<String>`

## Example:

```javascript
const fs = require('fs-extra')

// remove file
fs.removeSync('/tmp/myfile')

fs.removeSync('/home/jprichardson') // 我刚刚删除了整个HOME目录。
```
