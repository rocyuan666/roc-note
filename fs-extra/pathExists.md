# pathExists(file[, callback])

通过检查文件系统来测试给定路径是否存在。与[fs.exists](https://nodejs.org/api/fs.html#fs_fs_exists_path_callback)类似，但具有正常的回调签名（err，exists）。在引擎盖下使用fs.access。

- `file` `<String>`
- `callback` `<Function>` 
   - `err` `<Error>`
   - `exists` `<boolean>`

## Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/this/path/does/not/exist/file.txt'

// 使用回调:
fs.pathExists(file, (err, exists) => {
  console.log(err) // => null
  console.log(exists) // => false
})

// 使用 Promise:
fs.pathExists(file)
  .then(exists => console.log(exists)) // => false

// 使用 async/await:
async function example (f) {
  const exists = await fs.pathExists(f)

  console.log(exists) // => false
}

example(file)
```
