# ensureFile(file[, callback])

确保文件存在。如果请求创建的文件位于不存在的目录中，则会创建这些目录。如果该文件已经存在，则不会被修改。
**Alias:** `createFile()`

- `file` `<String>`
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/this/path/does/not/exist/file.txt'

// 使用回调：
fs.ensureFile(file, err => {
  console.log(err) // => null
  // 文件已创建，包括要放置的目录
})

// 使用 Promise:
fs.ensureFile(file)
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example (f) {
  try {
    await fs.ensureFile(f)
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}

example(file)
```
