# ensureFileSync(file)

确保文件存在。如果请求创建的文件位于不存在的目录中，则会创建这些目录。如果该文件已经存在，则不会被修改。

**Alias:** `createFileSync()`

- `file` `<String>`

## Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/this/path/does/not/exist/file.txt'
fs.ensureFileSync(file)
// 文件已创建，包括要放置的目录
```
