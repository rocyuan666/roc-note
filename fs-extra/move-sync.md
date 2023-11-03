# moveSync(src, dest[, options])

移动文件或目录，甚至跨设备移动。

- `src` `<String>`
- `dest` `<String>` 注意：当src是文件时，dest必须是文件，当src是目录时，dest必须是目录。
- `options` `<Object>` 
   - `overwrite` `<boolean>`: 覆盖现有文件或目录，默认值为false。

## Example:

```javascript
const fs = require('fs-extra')

fs.moveSync('/tmp/somefile', '/tmp/does/not/exist/yet/somefile')
```

**Using **`**overwrite**`** option**

```javascript
const fs = require('fs-extra')

fs.moveSync('/tmp/somedir', '/tmp/may/already/exist/somedir', { overwrite: true })
```
