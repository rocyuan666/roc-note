# ensureSymlinkSync(srcPath, destPath[, type])

确保符号链接存在。如果目录结构不存在，将创建它。

**Alias:** `createSymlinkSync()`

- `srcPath` `<String>`
- `destPath` `<String>`
- `type` `<String>`在Windows上可用，在其他平台上被忽略。它可以设置为dir、file或junction。

## Example:

```javascript
const fs = require('fs-extra')

const srcPath = '/tmp/file.txt'
const destPath = '/tmp/this/path/does/not/exist/file.txt'
fs.ensureSymlinkSync(srcPath, destPath)
// symlink现在已经创建，包括它要放置的目录
```
