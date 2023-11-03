# ensureLink(srcPath, destPath[, callback])

确保链接存在。如果目录结构不存在，将创建它。

**Alias:** `createLink()`

- `srcPath` `<String>`
- `destPath` `<String>`
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

const srcPath = '/tmp/file.txt'
const destPath = '/tmp/this/path/does/not/exist/file.txt'

// 使用回调：
fs.ensureLink(srcPath, destPath, err => {
  console.log(err) // => null
  // 链接现在已经创建，包括它要放置的目录
})

// 使用 Promise:
fs.ensureLink(srcPath, destPath)
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example (src, dest) {
  try {
    await fs.ensureLink(src, dest)
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}

example(srcPath, destPath)
```
