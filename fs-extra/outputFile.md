# outputFile(file, data[, options][, callback])

几乎与writeFile相同（即它覆盖），只是如果父目录不存在，则会创建它。文件必须是文件路径（不允许使用缓冲区或文件描述符）。

- `file` `<String>`
- `data` `<String> | <Buffer> | <Uint8Array>`
- `options` `<Object> | <String>` (与 `[fs.writeFile()](https://nodejs.org/api/fs.html#fs_fs_writefile_file_data_options_callback)`[ options](https://nodejs.org/api/fs.html#fs_fs_writefile_file_data_options_callback) 一样 )
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/this/path/does/not/exist/file.txt'

// 使用回调：
fs.outputFile(file, 'hello!', err => {
  console.log(err) // => null

  fs.readFile(file, 'utf8', (err, data) => {
    if (err) return console.error(err)
    console.log(data) // => hello!
  })
})

// 使用 Promise:
fs.outputFile(file, 'hello!')
.then(() => fs.readFile(file, 'utf8'))
.then(data => {
  console.log(data) // => hello!
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example (f) {
  try {
    await fs.outputFile(f, 'hello!')

    const data = await fs.readFile(f, 'utf8')

    console.log(data) // => hello!
  } catch (err) {
    console.error(err)
  }
}

example(file)
```
