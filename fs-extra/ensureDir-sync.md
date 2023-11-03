# ensureDirSync(dir[,options])

确保目录存在。如果目录结构不存在，将创建它。如果提供，选项可以指定目录的所需模式。

**Aliases:** `mkdirsSync()`, `mkdirpSync()`

- `dir` `<String>`
- `options` `<Integer> | <Object>` 
   - 如果为整数，则为模式。
   - 如果它是Object，它将是｛mode:＜Integer＞｝。

## Example:

```javascript
const fs = require('fs-extra')

const dir = '/tmp/this/path/does/not/exist'

const desiredMode = 0o2775
const options = {
  mode: 0o2775
}

fs.ensureDirSync(dir)
// dir现在已经创建，包括它要放置的目录

fs.ensureDirSync(dir, desiredMode)
// 现在已经创建了dir，包括它将被放置在具有0o2775权限的目录

fs.ensureDirSync(dir, options)
// 现在已经创建了dir，包括它将被放置在具有0o2775权限的目录
```
