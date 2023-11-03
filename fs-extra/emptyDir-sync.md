# emptyDirSync(dir)

确保目录为空。如果目录不为空，则删除目录内容。如果目录不存在，则创建该目录。目录本身不会被删除。

**Alias:** `emptydirSync()`

- `dir` `<String>`

## Example:

```javascript
const fs = require('fs-extra')

// 假设这个目录有很多文件和文件夹
fs.emptyDirSync('/tmp/some/dir')
```
