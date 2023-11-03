# outputJson(file, object[, options][, callback])

与writeJson几乎相同，只是如果目录不存在，则会创建它。

**Alias:** `outputJSON()`

- `file` `<String>`
- `object` `<Object>`
- `options` `<Object>` 
   - `spaces` `<Number> | <String>` 要缩进的空格数；或用于缩进的字符串（即传递“\t”用于制表符缩进）。有关更多信息，请[参阅文档](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify#The_space_argument)。
   - `EOL` `<String>` 设置EOL字符。默认值为\n。
   - `replacer` [JSON replacer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify#The_replacer_parameter)
   - 也接受 `[fs.writeFile()](https://nodejs.org/api/fs.html#fs_fs_writefile_file_data_options_callback)`[ options](https://nodejs.org/api/fs.html#fs_fs_writefile_file_data_options_callback)
- `callback` `<Function>` 
   - `err` `<Error>`

## Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/this/path/does/not/exist/file.json'

// 使用回调：
fs.outputJson(file, {name: 'JP'}, err => {
  console.log(err) // => null

  fs.readJson(file, (err, data) => {
    if (err) return console.error(err)
    console.log(data.name) // => JP
  })
})

// 使用 Promise:
fs.outputJson(file, {name: 'JP'})
.then(() => fs.readJson(file))
.then(data => {
  console.log(data.name) // => JP
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example (f) {
  try {
    await fs.outputJson(f, {name: 'JP'})

    const data = await fs.readJson(f)

    console.log(data.name) // => JP
  } catch (err) {
    console.error(err)
  }
}

example(file)
```
