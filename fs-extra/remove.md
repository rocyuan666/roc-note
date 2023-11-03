# remove(path[, callback])

删除文件或目录。目录可以包含内容。如果路径不存在，则不执行任何操作。

- `path` `<String>`
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

// remove file
// 使用回调:
fs.remove('/tmp/myfile', err => {
  if (err) return console.error(err)
  console.log('success!')
})

fs.remove('/home/jprichardson', err => {
  if (err) return console.error(err)
  console.log('success!') // 我刚刚删除了整个HOME目录。
})

// 使用 Promises:
fs.remove('/tmp/myfile')
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example (src, dest) {
  try {
    await fs.remove('/tmp/myfile')
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}

example()
```
