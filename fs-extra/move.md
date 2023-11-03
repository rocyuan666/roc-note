# move(src, dest[, options][, callback])

移动文件或目录，甚至跨设备移动。

- `src` `<String>`
- `dest` `<String>` 注意：当src是文件时，dest必须是文件，当src是目录时，dest必须是目录。
- `options` `<Object>` 
   - `overwrite` `<boolean>`: 覆盖现有文件或目录，默认值为false。
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

const src = '/tmp/file.txt'
const dest = '/tmp/this/path/does/not/exist/file.txt'

// 使用回调：
fs.move(src, dest, err => {
  if (err) return console.error(err)
  console.log('success!')
})

// 使用 Promise:
fs.move(src, dest)
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example (src, dest) {
  try {
    await fs.move(src, dest)
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}

example(src, dest)
```

**Using **`**overwrite**`** option**

```javascript
const fs = require('fs-extra')

fs.move('/tmp/somedir', '/tmp/may/already/exist/somedir', { overwrite: true }, err => {
  if (err) return console.error(err)
  console.log('success!')
})
```
