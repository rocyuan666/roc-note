# readJson(file[, options][, callback])

读取JSON文件，然后将其解析为对象。

**Alias:** `readJSON()`

- `file` `<String>`
- `options` `<Object>` (与 `[jsonFile.readFile()](https://github.com/jprichardson/node-jsonfile#readfilefilename-options-callback)`[ options](https://github.com/jprichardson/node-jsonfile#readfilefilename-options-callback)一样)
- `callback` `<Function>` 
   - `err` `<Error>`
   - `obj` `<Object>`

## Example:

```javascript
const fs = require('fs-extra')

// 使用回调：
fs.readJson('./package.json', (err, packageObj) => {
  if (err) console.error(err)
  console.log(packageObj.version) // => 0.1.3
})

// 使用 Promises:
fs.readJson('./package.json')
.then(packageObj => {
  console.log(packageObj.version) // => 0.1.3
})
.catch(err => {
  console.error(err)
})

// 使用 async/await:
async function example () {
  try {
    const packageObj = await fs.readJson('./package.json')
    console.log(packageObj.version) // => 0.1.3
  } catch (err) {
    console.error(err)
  }
}

example()
```

---

readJson（）可以接受设置为false的throws选项，如果JSON无效，则不会抛出。
Example:

```javascript
const fs = require('fs-extra')

const file = '/tmp/some-invalid.json'
const data = '{not valid JSON'
fs.writeFileSync(file, data)

// 使用回调：
fs.readJson(file, { throws: false }, (err, obj) => {
  if (err) console.error(err)
  console.log(obj) // => null
})

// 使用 Promise:
fs.readJson(file, { throws: false })
.then(obj => {
  console.log(obj) // => null
})
.catch(err => {
  console.error(err) // Not called
})

// 使用 async/await:
async function example (f) {
  const obj = await fs.readJson(f, { throws: false })
  console.log(obj) // => null
}

example(file)
```
