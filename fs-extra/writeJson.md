# writeJson(file, object[, options][, callback])

将对象写入JSON文件。

**Alias:** `writeJSON()`

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

// 使用回调:
fs.writeJson('./package.json', {name: 'fs-extra'}, err => {
  if (err) return console.error(err)
  console.log('success!')
})

// 使用 Promise:
fs.writeJson('./package.json', {name: 'fs-extra'})
.then(() => {
  console.log('success!')
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example () {
  try {
    await fs.writeJson('./package.json', {name: 'fs-extra'})
    console.log('success!')
  } catch (err) {
    console.error(err)
  }
}

example()
```

---

另请参见**:** `[outputJson()](outputJson.md)`
