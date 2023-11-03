# ensureSymlink(srcPath, destPath[, type][, callback])

确保符号链接存在。如果目录结构不存在，将创建它。

**Alias:** `createSymlink()`

- `srcPath` `<String>`
- `destPath` `<String>`
- `type` `<String>` 它仅在Windows上可用，在其他平台上被忽略。它可以设置为dir、file或junction。
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

const srcPath = '/tmp/file.txt'
const destPath = '/tmp/this/path/does/not/exist/file.txt'

// With a callback:
fs.ensureSymlink(srcPath, destPath, err => {
  console.log(err) // => null
  // symlink has now been created, including the directory it is to be placed in
})

// With Promises:
fs.ensureSymlink(srcPath, destPath)
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// With async/await:
async function example (src, dest) {
  try {
    await fs.ensureSymlink(src, dest)
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}

example(srcPath, destPath)
```
