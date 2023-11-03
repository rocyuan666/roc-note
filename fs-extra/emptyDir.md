# emptyDir(dir[, callback])

确保目录为空。如果目录不为空，则删除目录内容。如果目录不存在，则创建该目录。目录本身不会被删除。

**Alias:** `emptydir()`

- `dir` `<String>`
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

// 假设这个目录有很多文件和文件夹
// 使用回调：
fs.emptyDir('/tmp/some/dir', err => {
  if (err) return console.error(err)
  console.log('success!')
})

// 使用 Promise:
fs.emptyDir('/tmp/some/dir')
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example () {
  try {
    await fs.emptyDir('/tmp/some/dir')
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}

example()
```
