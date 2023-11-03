# ensureLinkSync(srcPath, destPath)

确保链接存在。如果目录结构不存在，将创建它。

**Alias:** `createLinkSync()`

- `srcPath` `<String>`
- `destPath` `<String>`

## Example:

```javascript
const fs = require('fs-extra')

const srcPath = '/tmp/file.txt'
const destPath = '/tmp/this/path/does/not/exist/file.txt'
fs.ensureLinkSync(srcPath, destPath)
// 链接现在已经创建，包括它要放置的目录
```
